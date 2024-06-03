public abstract class PersonagemDragonBall {
    protected String nome;
    protected int idade;
    protected String sexo;
    protected String temporada;
    protected int ki;
    protected String poderEspecial;

 public PersonagemDragonBall(String nome, int idade, String sexo, String temporada, int ki, String poderEspecial) {
        this.nome = nome;
        this.idade = idade;
        this.sexo = sexo;
        this.temporada = temporada;
        this.ki = ki;
        this.poderEspecial = poderEspecial;
    }

    public abstract int calcularPoder();
}
[19:44, 6/3/2024] Pretin: public interface Transformavel {
    void transformar(int nivel);
}
public class Terraqueo extends PersonagemDragonBall {
    private String pais;
    private String cidade;

    public Terraqueo(String nome, int idade, String sexo, String temporada, int ki, String poderEspecial, String pais, String cidade) {
        super(nome, idade, sexo, temporada, ki, poderEspecial);
        this.pais = pais;
        this.cidade = cidade;
    }

    @Override
    public int calcularPoder() {
        return ki;
    }

    @Override
    public String toString() {
        return "Terraqueo{" +
                "nome='" + nome + '\'' +
                ", idade=" + idade +
                ", sexo='" + sexo + '\'' +
                ", temporada='" + temporada + '\'' +
                ", ki=" + ki +
                ", poderEspecial='" + poderEspecial + '\'' +
                ", pais='" + pais + '\'' +
                ", cidade='" + cidade + '\'' +
                '}';
    }
}public class Sayajin extends PersonagemDragonBall implements Transformavel {
    private int nivelMaximoSSJ;
    private boolean temRabo;

    public Sayajin(String nome, int idade, String sexo, String temporada, int ki, String poderEspecial, int nivelMaximoSSJ, boolean temRabo) {
        super(nome, idade, sexo, temporada, ki, poderEspecial);
        this.nivelMaximoSSJ = nivelMaximoSSJ;
        this.temRabo = temRabo;
    }

    @Override
    public int calcularPoder() {
        return ki * (1 + nivelMaximoSSJ * 0.1);
    }

    @Override
    public void transformar(int nivel) {
        if (nivel >= 1 && nivel <= 3) {
            System.out.println(nome + " transformou para super sayajin nível " + nivel);
        } else if (nivel >= 4 && nivel <= 5 && (nome.equals("Goku") || nome.equals("Vegeta"))) {
            System.out.println(nome + " transformou para super sayajin nível " + nivel);
        } else {
            System.out.println("Não foi possível transformar esse sayajin");
        }
    }

    @Override
    public String toString() {
        return "Sayajin{" +
                "nome='" + nome + '\'' +
                ", idade=" + idade +
                ", sexo='" + sexo + '\'' +
                ", temporada='" + temporada + '\'' +
                ", ki=" + ki +
                ", poderEspecial='" + poderEspecial + '\'' +
                ", nivelMaximoSSJ=" + nivelMaximoSSJ +
                ", temRabo=" + temRabo +
                '}';
    }
}[19:44, 6/3/2024] Pretin: public class Sayajin extends PersonagemDragonBall implements Transformavel {
    private int nivelMaximoSSJ;
    private boolean temRabo;

    public Sayajin(String nome, int idade, String sexo, String temporada, int ki, String poderEspecial, int nivelMaximoSSJ, boolean temRabo) {
        super(nome, idade, sexo, temporada, ki, poderEspecial);
        this.nivelMaximoSSJ = nivelMaximoSSJ;
        this.temRabo = temRabo;
    }

    @Override
    public int calcularPoder() {
        return ki * (1 + nivelMaximoSSJ * 0.1);
    }

    @Override
    public void transformar(int nivel) {
        if (nivel >= 1 && nivel <= 3) {
            System.out.println(nome + " transformou para super sayajin nível " + nivel);
        } else if (nivel >= 4 && nivel <= 5 && (nome.equals("Goku") || nome.equals("Vegeta"))) {
            System.out.println(nome + " transformou para super sayajin nível " + nivel);
        } else {
            System.out.println("Não foi possível transformar esse sayajin");
        }
    }

    @Override
    public String toString() {
        return "Sayajin{" +
                "nome='" + nome + '\'' +
                ", idade=" + idade +
                ", sexo='" + sexo + '\'' +
                ", temporada='" + temporada + '\'' +
                ", ki=" + ki +
                ", poderEspecial='" + poderEspecial + '\'' +
                ", nivelMaximoSSJ=" + nivelMaximoSSJ +
                ", temRabo=" + temRabo +
                '}';
    }
}
[19:44, 6/3/2024] Pretin: import java.util.HashMap;
import java.util.Map;

public class Namekuseijin extends PersonagemDragonBall {
    private int quantidadeEsferas;
    private boolean podeCurar;

    public Namekuseijin(String nome, int idade, String sexo, String temporada, int ki, String poderEspecial, int quantidadeEsferas, boolean podeCurar) {
        super(nome, idade, sexo, temporada, ki, poderEspecial);
        this.quantidadeEsferas = quantidadeEsferas;
        this.podeCurar = podeCurar;
    }

    @Overridepublic int calcularPoder() {
        return ki * (1 + (podeCurar ? 0.2 : 0));
    }

    @Override
    public String toString() {
        return "Namekuseijin{" +
                "nome='" + nome + '\'' +
                ", idade=" + idade +
                ", sexo='" + sexo + '\'' +
                ", temporada='" + temporada + '\'' +
                ", ki=" + ki +
                ", poderEspecial='" + poderEspecial + '\'' +
                ", quantidadeEsferas=" + quantidadeEsferas +
                ", podeCurar=" + podeCurar +
                '}';
    }

    public String fazerDesejo(String desejo) {
        Map<String, String> tradutor = new HashMap<>();
        tradutor.put("imortalidade", "kamisama");
        tradutor.put("poder", "chikara");
        tradutor.put("riqueza", "takara");

        StringBuilder desejoTraduzido = new StringBuilder();
        for (String palavra : desejo.split(" ")) {
            desejoTraduzido.append(tradutor.getOrDefault(palavra, palavra)).append(" ");
        }
        return desejoTraduzido.toString().trim();
    }
}public class PersonagemFactory {
    public static PersonagemDragonBall criarPersonagem(String nome) {
        switch (nome) {
            case "Kuririn":
                return new Terraqueo("Kuririn", 35, "Masculino", "Z", 3000, "Kienzan", "Terra", "Cidade do Oeste");
            case "Goku":
                return new Sayajin("Goku", 40, "Masculino", "Super", 15000, "Kamehameha", 5, true);
            case "Gohan":
                return new Sayajin("Gohan", 23, "Masculino", "Super", 12000, "Masenko", 3, false);
            case "Dende":
                return new Namekuseijin("Dende", 200, "Masculino", "Z", 4000, "Curar", 7, true);
            default:
                return null;
        }
    }
}public class Main {
    public static void main(String[] args) {
        // Criação dos personagens usando a fábrica
        PersonagemDragonBall goku = PersonagemFactory.criarPersonagem("Goku");
        PersonagemDragonBall gohan = PersonagemFactory.criarPersonagem("Gohan");
        PersonagemDragonBall dende = PersonagemFactory.criarPersonagem("Dende");

        // Evolução do Goku para Super Sayajin 5
        if (goku instanceof Sayajin) {
            ((Sayajin) goku).transformar(5);
        }

        // Evolução do Gohan para Super Sayajin 5, se não for possível, evolua para nível 3
        if (gohan instanceof Sayajin) {
            ((Sayajin) gohan).transformar(5);
            ((Sayajin) gohan).transformar(3);
        }

        // Pedido das esferas do dragão usando o Dende
        if (dende instanceof Namekuseijin) {
            String desejo = "quero imortalidade e poder";
            String desejoTraduzido = ((Namekuseijin) dende).fazerDesejo(desejo);
            System.out.println("Desejo traduzido: " + desejoTraduzido);
        }
    }
}
