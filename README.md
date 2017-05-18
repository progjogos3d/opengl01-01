# Projeto base da aula 1


Este projeto contém o código base da aula 1. Ele já possui algumas implementações, descritas a seguir
 
# Instalação

## Aplicativos

Para executar os exemplos da aula você precisará:
 - Do JDK instalado, na versão 8. Você pode baixa-lo [aqui](http://www.oracle.com/technetwork/java/javase/downloads/index.html).
 - De uma IDE para desenvolvimento Java, preferencialmente o [IntelliJ Idea](https://www.jetbrains.com/idea/?fromMenu). 
 A Jetbrains libera a licença da versão premium para estudantes, porém, todos os exemplos rodam na versão community. 
 Outra alternativa é a IDE [Eclipse](https://www.eclipse.org/downloads/eclipse-packages/). Baixe o package 
 "for Java Developers", não utilizaremos os recursos da versão Enterprise, bem mais pesada.
 
 ## Bibliotecas

Utilizaremos as bibliotecas  [JOML](https://github.com/JOML-CI/JOML) e [LWJGL](https://www.lwjgl.org/). 

Elas podem ser automaticamente baixadas pela sua IDE, pois todos os projetos possuem um arquivo chamado pom.xml, que 
permite que o software [Maven](https://maven.apache.org/) (já integrado as IDEs sugeridas) as baixem.

 # Classe Window
  
A classe `Window` abre a janela principal da aplicação utilizando a biblioteca glfw e controla o game loop. Ela possui 
os seguintes métodos:
- init(): Inicializa as propriedades iniciais da janela, tal como seu tamanho ou posição, se será ou não 
redimensionável, qual será a classe que receberá eventos de teclado, e qual será a versão de OpenGL utilizada 
(no caso 3.3)
- loop(): Executa o game loop. Calcula o tempo entre updates e realiza a troca dos buffers. Dispara os eventos de init, 
 update, draw e deInit da cena.
- show(): Chama os métodos init() e draw() e faz um tratamento básico de erros.

A classe `Window` foi organizada de modo que toda lógica da scena seja implementada numa classe filha da interface 
`Scene`.

# Scene

Essa interface impõe a implementação de 4 métodos:

- Init: Onde será feita a carga dos recursos e inicialização básica da janela
- Update: Atualiza a lógica do game. O método recebe como parâmetro o tempo entre dois quadros, em segundos
- Draw: Realiza o desenho da cena
- DeInit: Descarrega recursos.

A classe Triangle.java, que conterá o código da aula é uma implementação da interface Scene.

#Keyboard

Trata-se de uma classe auxiliar para armazenar que teclas foram pressionadas. Um exemplo de seu uso está no método 
update da classe Window

#Classe Triangle

Por fim, o projeto contém a classe Triangle. Trata-se de uma implementação de Scene, onde desenharemos o primeiro 
triangulo. Neste projeto a classe contém apenas o código para definir a cor de limpeza de tela no método init, e uma
implementação para a janela fechar ao se pressionar ESC no método update. 

É nessa classe que iremos trabalhar. Atualmente, ela simplesmente abre uma janela preta, sem desenho algum.

#Outros detalhes

Em nosso curso, implementaremos código em dois pacotes `br.pucpr.mage`, que conterá nosso motor gráfico, chamado de 
Micro Academic Graphics Engine (MAGE). 

E o pacote `br.pucpr.cg` que contém o código que o programador, que utiliza o nosso motor, criará. Ao desenvolver, 
imagine que quem desenvolve os dois pacotes são equipes diferentes. Como se ao desenvolvermos o pacote mage fossemos
o fabricante da Unity, e ao desenvolvermos o pacote cg fomos o game developer que usa a Unity.

Ao final de nosso curso, teremos um motor gráfico bastante simples, mas que esclarecerá para você bastante sobre como
a placa de vídeo e engines como a Unity funcionam.