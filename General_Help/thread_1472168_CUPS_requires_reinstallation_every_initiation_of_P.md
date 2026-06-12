---
title: "CUPS requires reinstallation every initiation of PC"
date: 2010-05-04
forum: General Help
---

### Post by Nemex1975 on 2010-05-04
First, in English, after in Portuguese (at end, the reply from the Cups Team):

I have the ubuntu 10.04.
Good morning.
I do not know if this place would be more appropriate to report this problem I'm having, but I think better here than on the topic of the news about the release of Ubuntu 10.04.
It is this: every time I turn off my PC and restarting printers are not detected. To be able to use them I have to reinstall all applications cups, then function normally. But to shut down the PC settings are lost, although the files "cups" still installed.
I use an HP deskjet 5440 and a HP laserjet 1015.
With the same PC and even Ubuntu 9.10 and it never happened, as I am User since version 7.10, is already three years of use without this oddity happen.
Does anyone have any report about this bug in Ubuntu does not recognize the printers, reinstall the files need to make cups work?
Is there anything I can do with some configuration or script to solve the problem?
Grateful for the attention.
Nemex1975
===
Continuing the undesirable discoveries ...
Good morning.

If it helps in solving the problem, I tried to put in applications meeting the following parameter: / usr / sbin / cupsd because when I try to print anything appears just a message "print to file" and when I go into System-> Administration -> Print manager is even with the "configuration" is available ... I click "connect" (with the server cups) and a message appears saying that he is not running ... go to "system monitor" and it actually is not listed. Only works even if I reinstall the cups every time you turn on the PC.
It tried to see if the same happened with VirtualBox, but different from my PC, after I configured the same printer HP Laserjet 1015 at 10:04 ubuntu virtual machine, it is not losing the configuration. Every time I start the VB printer setup is already there, as it was in 9.04.

I just like to understand why even putting in applications cupsd will not start this session alone. And because in Sun VB, just connecting the printer, it has already done all the work, installed my printer and keep the installation configuration intact.
Messages that appear say that I have to install the dkms ... it has always been installed ...says I need the hplip ... he was always there.
Imagine if one day my Internet is down and I need to print something urgent: can I just do not.

[SIZE=4]**THE CUPS TEAM REPLY**[/SIZE]:
Please contact your Linux distributor for this issue.

It  sounds like there is a problem with their CUPS packaging...

I would recommend that you contact Ubuntu and get a fixed package  from them - there are a bunch of patches they apply that would be lost,  potentially making the problem worse than it is now...

mike (Michael Sweet)
11:08 May 03, 2010

Link: [http://www.cups.org/str.php?L3575](http://www.cups.org/str.php?L3575)
STR #3575

_**PORTUGUESE**_:
[I]Bom dia.
Eu não sei se este  local seria o mais apropriado para relatar este problema que estou  tendo, mas acho melhor aqui do que no tópico da notícia sobre o  lançamento do Ubuntu 10.04.
É o seguinte: toda vez que eu desligo o  meu PC e religo as impressoras não são detectadas. Para conseguir  usá-las eu tenho de reinstalar todos os aplicativos cups, daí funcionam  normalmente. Mas ao desligar o PC as configurações se perdem, apesar de  os arquivos "cups" continuarem instalados.
Eu uso uma HP deskjet 5440  e uma HP laserjet 1015.
Com o mesmo PC e até o Ubuntu 9.10 isso  nunca aconteceu e, como sou usuário desde a versão 7.10, já são 3 anos  de uso sem que essa esquisitice acontecesse.
Alguém tem algum relato  sobre este bug de o Ubuntu não reconhecer as impressoras, necessitando  reinstalar os arquivos cups para fazer funcionar?
Há algo que eu  possa fazer com algum script ou configuração para solucionar o problema?
Grato  pela atenção.
Nemex1975
===
Continuando as indesejáveis  descobertas...
Bom dia.

Se ajuda na solução do problema, eu  tentei colocar nos aplicativos de sessão o seguinte parâmetro:  /usr/sbin/cupsd pois quando eu tento imprimir qualquer coisa aparece  apenas uma mensagem de "imprimir para arquivo" e quando eu vou em  Sistema->Administração->Impressão o gerenciador sequer fica com a  opção "configuração" disponível... eu clico em "conectar" (com o  servidor cups) e aparece uma mensagem dizendo que ele não está em  execução... vou ao "monitor do sistema" e ele de fato não está listado.  Só funciona mesmo se eu reinstalar o cups a cada vez que ligar o PC.
Daí  tentei ver se o mesmo acontecia com a VirtualBox mas, diferente do meu  PC, depois que eu configurei a mesma impressora HP Laserjet 1015 no  ubuntu 10.04 da máquina virtual, ele não está perdendo a configuração.  Toda vez que inicio a VB a configuração da impressora já está lá, como  estava no 9.04.
Eu só gostaria de entender porque nem mesmo colocando o cupsd nos aplicativos de sessão essa porcaria não inicia sozinha. E porque na VB, apenas ligando a impressora, ela já fez todo o trabalho, instalou minha impressora e mantém a configuração de instalação intacta.
As mensagens que aparecem dizem que eu tenho que instalar o dkms... ele sempre esteve instalado... diz que necessito do hplip... ele também sempre esteve lá.
Imagina se um dia minha Internet estiver inoperante e eu precisar imprimir algo urgente: simplesmente não poderei.
[/I]

---

### Post by FluidFiftyOne on 2010-05-04
I'm having a similar issue here...
and I hope someone finds a solution


for a start you say that you reinstall .. instead of that you could just go to terminal and write

sudo /etc/init.d/cups start

and it will start working, but this is not a permanent solution...

I will also put a few lines of my /var/log/cups/error_log  here 
maybe someone will know how to make cups start at boot again.

E [04/May/2010:13:56:21 +0200] Unable to remove temporary file "/var/spool/cups/tmp/.fontconfig" - Is a directory
E [04/May/2010:13:56:21 +0200] Unable to remove temporary file "/var/spool/cups/tmp/.hplip" - Is a directory
E [04/May/2010:14:23:19 +0200] Unable to remove temporary file "/var/spool/cups/tmp/.fontconfig" - Is a directory
E [04/May/2010:14:23:19 +0200] Unable to remove temporary file "/var/spool/cups/tmp/.hplip" - Is a directory
E [04/May/2010:14:24:37 +0200] Unable to remove temporary file "/var/spool/cups/tmp/.fontconfig" - Is a directory
E [04/May/2010:14:24:37 +0200] Unable to remove temporary file "/var/spool/cups/tmp/.hplip" - Is a directory
E [04/May/2010:14:28:07 +0200] Unable to remove temporary file "/var/spool/cups/tmp/.fontconfig" - Is a directory


thanx

---

### Post by Nemex1975 on 2010-05-05
Thanks for the tip of the Terminal, FluidFiftyOne ... worked.

It's possible someone make a **script** to automate this function **Cups** and **VirtualBox** until the final solution of the problem? If possible, someone could post here to avoid that have Terminal open all the time?
I would also like to know what **command** to put these functions starting Cups and VirtualBox in **applications of session** (System - preferences - Application Session), which would be easier than creating a script.
Grateful.

Portugues:
Obrigado pela dica do Terminal, FluidFiftyOne... deu certo.
É possível fazer um **script** para automatizar esta função do **Cups** e do **VirtualBox** até a solução definitiva do problema? Se for possível, alguém poderia postar aqui para evitar que tenhamos de abrir Terminal a todo momento?
E também gostaria de saber qual o **comando** para colocar estas funções de iniciar o Cups e o VirtualBox nos **aplicativos de sessão** (Sistema - preferência - aplicativos de sessão), o que seria mais fácil do que criar um script.
Grato.

---

