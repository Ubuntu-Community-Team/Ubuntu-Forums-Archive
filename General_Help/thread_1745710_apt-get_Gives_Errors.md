---
title: "apt-get Gives Errors"
date: 2011-05-01
forum: General Help
---

### Post by 42turkeys on 2011-05-01
Hi,

Whenever I try to do anything in apt-get, such as 'apt-get update', it comes up with an error like this:
> Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

Please could someone help me fix this :)

Thanks!

---

### Post by samigina on 2011-05-01
Same problem here.

---

### Post by samigina on 2011-05-01
Found the soultion, run in a terminal:

sudo rm /var/lib/apt/lists/* -vf
and then
sudo apt-get update

---

### Post by 42turkeys on 2011-05-01
Worked for me to, thanks so much! :)

---

### Post by vaqomega on 2011-05-02
> **samigina said:**
> Found the soultion, run in a terminal:

sudo rm /var/lib/apt/lists/* -vf
and then
sudo apt-get update

It didn't work for me, it seems that i messed something, here's my error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/co.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages, E:No se pudieron analizar o abrir las listas de paquetes o el archivo de estado.'

and there's a red circle with awhiite line in the top of my desktop showing that error, what can i do?:confused::confused::confused::confused:

---

### Post by samigina on 2011-05-12
Hola, veo que hablas español, debes ejecutar los comandos en una terminal.

Abre una terminal y escribe:
sudo rm /var/lib/apt/lists/* -vf

Luego:

sudo apt-get update

---

