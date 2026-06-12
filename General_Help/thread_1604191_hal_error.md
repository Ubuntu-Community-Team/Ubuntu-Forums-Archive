---
title: "hal error"
date: 2010-10-23
forum: General Help
---

### Post by ultra_PT on 2010-10-23
When i try to install anything in ubuntu 10.10 i get this:

sudo apt-get install sl
A ler as listas de pacotes... Pronto
A construir árvore de dependências       
A ler a informação de estado... Pronto
sl já está na versão mais recente.
0 pacotes actualizados, 0 pacotes novos instalados, 0 a remover e 16 não actualizados.
1 pacotes não totalmente instalados ou removidos.
Após esta operação, serão utilizados 0B adicionais de espaço em disco.
Deseja continuar [Y/n]? y
A instalar hal (0.5.14-0ubuntu6) ...
useradd: não é possível bloquear /etc/passwd, tente novamente mais tarde
adduser: `/usr/sbin/useradd -d /var/run/hald -g haldaemon -s /bin/false -u 117 haldaemon' retornou o erro de código 1. Saindo.
dpkg: erro ao processar hal (--configure):
 subprocesso instalado o programa post-installation retornou erro do status de saída 1
Foram encontrados erros enquanto processava:
 hal
E: Sub-process /usr/bin/dpkg returned an error code (1)


I've tried to look around for solutions, but with no luck :(

Can anyone help?

---

### Post by sikander3786 on 2010-10-23
Try

```
sudo dpkg --configure -a
```

And post the output if it contains errors.

---

### Post by ultra_PT on 2010-10-23
> **sikander3786 said:**
> Try

```
sudo dpkg --configure -a
```

And post the output if it contains errors.

sudo dpkg --configure -a
A instalar hal (0.5.14-0ubuntu6) ...
useradd: não é possível bloquear /etc/passwd, tente novamente mais tarde
adduser: `/usr/sbin/useradd -d /var/run/hald -g haldaemon -s /bin/false -u 117 haldaemon' retornou o erro de código 1. Saindo.
dpkg: erro ao processar hal (--configure):
 subprocesso instalado o programa post-installation retornou erro do status de saída 1
Foram encontrados erros enquanto processava:
 hal


It seems like i always get the same error, no matter what i do :s

---

### Post by sikander3786 on 2010-10-23
Ok.

```
sudo apt-get install --reinstall hal
```

If it doesn't work, try to purge the package and then reinstall.

```
sudo apt-get remove --purge hal
```

```
sudo apt-get install hal
```

```
sudo apt-get install -f
```

---

### Post by ultra_PT on 2010-10-23
sudo apt-get install --reinstall hal
A ler as listas de pacotes... Pronto
A construir árvore de dependências       
A ler a informação de estado... Pronto
0 pacotes actualizados, 0 pacotes novos instalados, 1 reinstalados, 0 a remover e 0 não actualizados.
1 pacotes não totalmente instalados ou removidos.
Após esta operação, serão utilizados 0B adicionais de espaço em disco.
A instalar hal (0.5.14-0ubuntu6) ...
useradd: não é possível bloquear /etc/passwd, tente novamente mais tarde
adduser: `/usr/sbin/useradd -d /var/run/hald -g haldaemon -s /bin/false -u 117 haldaemon' retornou o erro de código 1. Saindo.
dpkg: erro ao processar hal (--configure):
 subprocesso instalado o programa post-installation retornou erro do status de saída 1
Foram encontrados erros enquanto processava:
 hal
E: Sub-process /usr/bin/dpkg returned an error code (1)

sudo apt-get remove --purge hal
A ler as listas de pacotes... Pronto
A construir árvore de dependências       
A ler a informação de estado... Pronto
Serão REMOVIDOS os seguintes pacotes:
  hal*
0 pacotes actualizados, 0 pacotes novos instalados, 1 a remover e 0 não actualizados.
1 pacotes não totalmente instalados ou removidos.
Após esta operação, será libertado 1810kB de espaço em disco.
Deseja continuar [Y/n]? y
(A ler a base de dados ... 147101 ficheiros e directórios actualmente instalados.)
A remover hal ...
A purgar os ficheiros de configuração para hal ...
rmdir: erro ao remover `/var/cache/hald': Ficheiro ou directoria inexistente
rmdir: erro ao remover `/var/run/hald': Ficheiro ou directoria inexistente
A processar 'triggers' para man-db ...

sudo apt-get install hal
A ler as listas de pacotes... Pronto
A construir árvore de dependências       
A ler a informação de estado... Pronto
Pacotes sugeridos:
  gnome-device-manager
Serão instalados os seguintes NOVOS pacotes:
  hal
0 pacotes actualizados, 1 pacotes novos instalados, 0 a remover e 0 não actualizados.
É necessário obter 0B/382kB de arquivos.
Após esta operação, serão utilizados 1810kB adicionais de espaço em disco.
A seleccionar pacote anteriormente não seleccionado hal
(A ler a base de dados ... 146971 ficheiros e directórios actualmente instalados.)
A descompactar hal (desde .../hal_0.5.14-0ubuntu6_amd64.deb) ...
A processar 'triggers' para man-db ...
A instalar hal (0.5.14-0ubuntu6) ...
useradd: não é possível bloquear /etc/passwd, tente novamente mais tarde
adduser: `/usr/sbin/useradd -d /var/run/hald -g haldaemon -s /bin/false -u 117 haldaemon' retornou o erro de código 1. Saindo.
dpkg: erro ao processar hal (--configure):
 subprocesso instalado o programa post-installation retornou erro do status de saída 1
Foram encontrados erros enquanto processava:
 hal
E: Sub-process /usr/bin/dpkg returned an error code (1)

sudo apt-get install -f
A ler as listas de pacotes... Pronto
A construir árvore de dependências       
A ler a informação de estado... Pronto
0 pacotes actualizados, 0 pacotes novos instalados, 0 a remover e 0 não actualizados.
1 pacotes não totalmente instalados ou removidos.
Após esta operação, serão utilizados 0B adicionais de espaço em disco.
A instalar hal (0.5.14-0ubuntu6) ...
useradd: não é possível bloquear /etc/passwd, tente novamente mais tarde
adduser: `/usr/sbin/useradd -d /var/run/hald -g haldaemon -s /bin/false -u 117 haldaemon' retornou o erro de código 1. Saindo.
dpkg: erro ao processar hal (--configure):
 subprocesso instalado o programa post-installation retornou erro do status de saída 1
Foram encontrados erros enquanto processava:
 hal
E: Sub-process /usr/bin/dpkg returned an error code (1)


:(

---

### Post by sikander3786 on 2010-10-23
Can you please change the language to English and re-run those commands. I forgot to mention that in my last post but the errors might be informative here.

---

### Post by ultra_PT on 2010-10-23
There you go:

sudo apt-get install --reinstall hal
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up hal (0.5.14-0ubuntu6) ...
useradd: cannot lock /etc/passwd; try again later.
adduser: `/usr/sbin/useradd -d /var/run/hald -g haldaemon -s /bin/false -u 117 haldaemon' returned error code 1. Exiting.
dpkg: error processing hal (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 hal
E: Sub-process /usr/bin/dpkg returned an error code (1)

sudo apt-get remove --purge hal
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  hal*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 1,810kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 153318 files and directories currently installed.)
Removing hal ...
Purging configuration files for hal ...
rmdir: failed to remove `/var/cache/hald': No such file or directory
rmdir: failed to remove `/var/run/hald': No such file or directory
Processing triggers for man-db ...

sudo apt-get install hal
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  gnome-device-manager
The following NEW packages will be installed:
  hal
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/382kB of archives.
After this operation, 1,810kB of additional disk space will be used.
Selecting previously deselected package hal.
(Reading database ... 153188 files and directories currently installed.)
Unpacking hal (from .../hal_0.5.14-0ubuntu6_amd64.deb) ...
yProcessing triggers for man-db ...
Setting up hal (0.5.14-0ubuntu6) ...
useradd: cannot lock /etc/passwd; try again later.
adduser: `/usr/sbin/useradd -d /var/run/hald -g haldaemon -s /bin/false -u 117 haldaemon' returned error code 1. Exiting.
dpkg: error processing hal (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 hal
E: Sub-process /usr/bin/dpkg returned an error code (1)

sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up hal (0.5.14-0ubuntu6) ...
useradd: cannot lock /etc/passwd; try again later.
adduser: `/usr/sbin/useradd -d /var/run/hald -g haldaemon -s /bin/false -u 117 haldaemon' returned error code 1. Exiting.
dpkg: error processing hal (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 hal
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by sikander3786 on 2010-10-23
In fact, the problem lies here.

> useradd: cannot lock /etc/passwd; try again later.

Did you try a simple reboot and retry installation? Might be some hung useradd or update manager, apt-get or synaptic process causing problems.

---

### Post by ultra_PT on 2010-10-23
yes, i've rebooted twice by now and every time i try to install anything i get the same error. :-?

---

### Post by ultra_PT on 2010-10-23
I think i solved it, thanks to a similar error in other thread -> [http://ubuntuforums.org/showthread.php?p=9468367](http://ubuntuforums.org/showthread.php?p=9468367) :)

Just this this:
```
sudo rm -f /etc/gshadow.lock /etc/shadow.lock /etc/passwd.lock
```

And then reinstalled hal. It worked with no errors. Hopefully it will stay the same way when i reboot :)

Anyway, thanks for all the help **sikander3786**, it helped me a lot ;)

---

