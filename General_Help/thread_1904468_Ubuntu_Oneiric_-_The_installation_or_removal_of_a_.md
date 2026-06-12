---
title: "Ubuntu Oneiric - The installation or removal of a software package failed"
date: 2012-01-04
forum: General Help
---

### Post by Kaiserfilk on 2012-01-04
I removed manually emacs folder on \usr\share (I know, it's bad...) but now I have a problem when I want to install and remove a software.


The command 

*sudo dpkg --configure -a*

gave :


razik@razik-VGN-FW31ZJ:~$ sudo dpkg --configure -a
[sudo] password for razik: 
Sorry, try again.
[sudo] password for razik: 
Paramétrage de emacs23-lucid (23.3+1-1ubuntu4) ...
emacs-install emacs23
install/dictionaries-common: Byte-compiling for emacsen flavour emacs23
Warning: Lisp directory `/usr/share/emacs/23.3/site-lisp' does not exist.
Warning: Lisp directory `/usr/share/emacs/site-lisp' does not exist.
Warning: Lisp directory `/usr/share/emacs/23.3/leim' does not exist.
Warning: Lisp directory `/usr/share/emacs/23.3/lisp' does not exist.
Warning: Lisp directory `/usr/share/emacs/23.3/leim' does not exist.
Error: charsets directory (/usr/share/emacs/23.3/etc/charsets) does not exist.
Emacs will not function correctly without the character map files.
Please check your installation!
Warning: Could not find simple.el nor simple.elc
Cannot open load file: bytecomp
emacs-install: /usr/lib/emacsen-common/packages/install/dictionaries-common emacs23 failed at /usr/lib/emacsen-common/emacs-install line 28, <TSORT> line 3.
dpkg*: erreur de traitement de emacs23-lucid (--configure)*:
 le sous-processus script post-installation installé a retourné une erreur de sortie d'état 255
Paramétrage de xemacs21-mule (21.4.22-3.1ubuntu1) ...
emacs-install xemacs21
install/dictionaries-common: Byte-compiling for emacsen flavour xemacs21
Compiling /usr/share/xemacs21/site-lisp/dictionaries-common/debian-ispell.el...
>>Error occurred processing debian-ispell.el: Opening input file: No such file or directory, /usr/share/xemacs21/site-lisp/dictionaries-common/debian-ispell.el

Compiling /usr/share/xemacs21/site-lisp/dictionaries-common/ispell.el...
>>Error occurred processing ispell.el: Opening input file: No such file or directory, /usr/share/xemacs21/site-lisp/dictionaries-common/ispell.el

Compiling /usr/share/xemacs21/site-lisp/dictionaries-common/flyspell.el...
>>Error occurred processing flyspell.el: Opening input file: No such file or directory, /usr/share/xemacs21/site-lisp/dictionaries-common/flyspell.el

Done
emacs-install: /usr/lib/emacsen-common/packages/install/dictionaries-common xemacs21 failed at /usr/lib/emacsen-common/emacs-install line 28, <TSORT> line 3.
dpkg*: erreur de traitement de xemacs21-mule (--configure)*:
 le sous-processus script post-installation installé a retourné une erreur de sortie d'état 1
dpkg*: des problèmes de dépendances empêchent la configuration de xemacs21*:
 xemacs21 dépend de xemacs21-mule (>= 21.4.22-3.1ubuntu1) | xemacs21-mule-canna-wnn (>= 21.4.22-3.1ubuntu1) | xemacs21-nomule (>= 21.4.22-3.1ubuntu1)*; cependant*:
 Le paquet xemacs21-mule n'est pas encore configuré.
  Le paquet xemacs21-mule-canna-wnn n'est pas installé.
  Le paquet xemacs21-nomule n'est pas installé.
dpkg*: erreur de traitement de xemacs21 (--configure)*:
 problèmes de dépendances - laissé non configuré
Des erreurs ont été rencontrées pendant l'exécution*:
 emacs23-lucid
 xemacs21-mule
 xemacs21
razik@razik-VGN-FW31ZJ:~$

---

### Post by imachavel on 2012-01-04
***************

---

### Post by Kaiserfilk on 2012-01-04
Thank you for the reply.

I finally removed the four programs by the following command (in /usr/share folder):

*sudo apt-get remove emacs emacs23-lucid xemacs21-mule xemacs21*

It didn't work when I was triying to remove them one by one.

Problem fixed !

---

