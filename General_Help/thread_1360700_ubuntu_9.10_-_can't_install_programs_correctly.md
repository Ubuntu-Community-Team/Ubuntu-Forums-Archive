---
title: "ubuntu 9.10 - can't install programs correctly"
date: 2009-12-21
forum: General Help
---

### Post by Teresa_ on 2009-12-21
I'm not new to ubuntu , but in this new version I can't seem to install programs correctly for example , If i try to intall GRKpod , I get a message saying that the installation has failed , and when I view the details I get this :

 > installArchives() failed: 
A seleccionar pacote anteriormente não seleccionado gtkpod 
(A ler a base de dados ... 
 (A ler a base de dados ... 5%
 (A ler a base de dados ... 10%
 (A ler a base de dados ... 15% (A ler a base de dados ... 20% 
(A ler a base de dados ... 25%
 (A ler a base de dados ... 30% 
(A ler a base de dados ... 35% 
(A ler a base de dados ... 40%
 (A ler a base de dados ... 45%
 (A ler a base de dados ... 50%
 (A ler a base de dados ... 55% 
(A ler a base de dados ... 60%
 (A ler a base de dados ... 65%
 (A ler a base de dados ... 70%
 (A ler a base de dados ... 75% 
(A ler a base de dados ... 80%
 (A ler a base de dados ... 85%
 (A ler a base de dados ... 90% 
(A ler a base de dados ... 95%
 (A ler a base de dados ... 100% 
(A ler a base de dados ... 197770 ficheiros e directórios actualmente instalados.) 
A descompactar gtkpod (desde .../gtkpod_0.99.14-2ubuntu3_i386.deb) ... 
A instalar ttf-mscorefonts-installer (3.0) ... 
 
These fonts were provided by Microsoft "in the interest of cross- 
platform compatibility".  This is no longer the case, but they are 
still available from third parties. 
 
You are free to download these fonts and use them for your own use, 
but you may not redistribute them in modified form, including changes 
to the file name or packaging format. 
 
Erro ao analisar URL [http://:8080/](http://:8080/) do 'proxy': Nome de máquina inválido. 
Erro ao analisar URL [http://:8080/](http://:8080/) do 'proxy': Nome de máquina inválido. 
Erro ao analisar URL [http://:8080/](http://:8080/) do 'proxy': Nome de máquina inválido. 
Erro ao analisar URL [http://:8080/](http://:8080/) do 'proxy': Nome de máquina inválido. 
Erro ao analisar URL [http://:8080/](http://:8080/) do 'proxy': Nome de máquina inválido. 
Erro ao analisar URL [http://:8080/](http://:8080/) do 'proxy': Nome de máquina inválido. 
Erro ao analisar URL [http://:8080/](http://:8080/) do 'proxy': Nome de máquina inválido. 
Erro ao analisar URL [http://:8080/](http://:8080/) do 'proxy': Nome de máquina inválido. 
Erro ao analisar URL [http://:8080/](http://:8080/) do 'proxy': Nome de máquina inválido. 
Erro ao analisar URL [http://:8080/](http://:8080/) do 'proxy': Nome de máquina inválido. 
Erro ao analisar URL [http://:8080/](http://:8080/) do 'proxy': Nome de máquina inválido. 
Erro ao analisar URL [http://:8080/](http://:8080/) do 'proxy': Nome de máquina inválido. 
sha256sum: andale32.exe: Ficheiro ou directoria inexistente 
andale32.exe: FALHOU a abrir ou ler 
sha256sum: AVISO:  1 de 1 ficheiro listado não pode ser lido 
Checksum mismatch for andale32.exe, aborting! 
dpkg: erro ao processar ttf-mscorefonts-installer (--configure): 
 subprocesso instalado o programa post-installation retornou erro do status de saída 1 
A instalar gtkpod (0.99.14-2ubuntu3) ... 
 
Foram encontrados erros enquanto processava: 
 ttf-mscorefonts-installer 



I get the same error in every program I try to install , the program itself is installed and it initiates correctly , but it fails in some actions.
So is there a solution?

---

### Post by Darael on 2009-12-21
You've got a proxy set, one which doen't actually exist. Try running the following before you try to install something again:```
export http_proxy=
```
Yes, there's meant to be nothing following the =.
If that doesn't work, try the same thing but with sudo.

---

