---
title: "kernel 2.6.16/2.6.17 &amp; fglrx"
date: 2006-06-19
forum: General Help
---

### Post by ehula on 2006-06-19
I am unable to get the fglrx accelerated ATI drivers working on kernels I have compiled from source, both 2.6.16 and 2.6.17. The installation of the image and headers packages goes fine, but when I try to install the fglrx-kernel package, I get the following:

/usr/src$ sudo dpkg -i fglrx-kernel-2.6.17-ck1_8.25.18-1+ck1_i386.deb
Password:
Selecting previously deselected package fglrx-kernel-2.6.17-ck1.
(Reading database ... 193963 files and directories currently installed.)
Unpacking fglrx-kernel-2.6.17-ck1 (from fglrx-kernel-2.6.17-ck1_8.25.18-1+ck1_i386.deb) ...
dpkg: dependency problems prevent configuration of fglrx-kernel-2.6.17-ck1:
 fglrx-kernel-2.6.17-ck1 depends on xorg-driver-fglrx (= 8.25.18-1); however:
  Version of xorg-driver-fglrx on system is 7.0.0-8.25.18+2.6.15.11-2.
dpkg: error processing fglrx-kernel-2.6.17-ck1 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 fglrx-kernel-2.6.17-ck1

Can anyone help me get the fglrx driver working on 2.6.16 or 2.6.17?

---

### Post by glotz on 2006-06-19
Have you installed the linux-restricted-modules-2.6.16/7-whatever packages?

---

### Post by xXx 0wn3d xXx on 2006-06-19
> **ehula]I am unable to get the fglrx accelerated ATI drivers working on kernels I have compiled from source, both 2.6.16 and 2.6.17. The installation of the image and headers packages goes fine, but when I try to install the fglrx-kernel package, I get the following:

/usr/src$ sudo dpkg -i fglrx-kernel-2.6.17-ck1_8.25.18-1+ck1_i386.deb
Password:
Selecting previously deselected package fglrx-kernel-2.6.17-ck1.
(Reading database ... 193963 files and directories currently installed.)
Unpacking fglrx-kernel-2.6.17-ck1 (from fglrx-kernel-2.6.17-ck1_8.25.18-1+ck1_i386.deb) ...
dpkg: dependency problems prevent configuration of fglrx-kernel-2.6.17-ck1:
 fglrx-kernel-2.6.17-ck1 depends on xorg-driver-fglrx (= 8.25.18-1) said:**
> 
Try not installing that fglrx file and try this:
[QUOTE]sudo apt-get install fglrx-kernel-source
This will build fglrx on an custom kernel. You will not have to recompile.

---

### Post by ehula on 2006-06-19
[QUOTE=glotz]Have you installed the linux-restricted-modules-2.6.16/7-whatever packages?[/QUOTE]
No I haven't because they don't exist. I have installed fglrx-kernel-source as per another thread, but that didn't seem to do anything.

---

### Post by ehula on 2006-06-19
[QUOTE=xXx 0wn3d xXx]Try not installing that fglrx file and try this:

This will build fglrx on an custom kernel. You will not have to recompile.[/QUOTE]
As I just stated (while you were composing your messge) I have already tried that, but it doesn't work. Am I missing anything?

---

### Post by xXx 0wn3d xXx on 2006-06-19
[QUOTE=ehula]As I just stated (while you were composing your messge) I have already tried that, but it doesn't work. Am I missing anything?[/QUOTE]
Try removing the xorg-driver-fglrx and fglrx-kernel-source and the reinstalling fglrx-kernel-source. I know this has worked for some people.

---

### Post by Rui Pais on 2006-06-19
hi,
or try the latest drivers directly from ATI:
[https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27]("https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27")

---

### Post by ehula on 2006-06-19
[QUOTE=xXx 0wn3d xXx]Try removing the xorg-driver-fglrx and fglrx-kernel-source and the reinstalling fglrx-kernel-source. I know this has worked for some people.[/QUOTE]
Just tried that, and it didn't work for me.

Any other suggestions?

BTW, I am not reconfiguring my xserver at all. I am leaving xorg.conf intact as per my 2.6.15 installation. Should that be OK?

---

### Post by hfdragon on 2006-07-23
I have one suggestion, but I find it UGLY ;-)

```
sudo dpkg -i --force-depends fglrx-*2.6.17*.deb
```

It forces the installation and configures the driver... and I now have no problems running Xgl/compiz ;-)

```
The error message :

Sélection du paquet fglrx-kernel-2.6.17 précédemment désélectionné.
(Lecture de la base de données... 139160 fichiers et répertoires déjà installés.)
Dépaquetage de fglrx-kernel-2.6.17 (à partir de fglrx-kernel-2.6.17_8.25.18-1+686_i386.deb) ...
dpkg : fglrx-kernel-2.6.17 : problèmes de dépendances, mais configuration comme demandé :
 fglrx-kernel-2.6.17 dépend de xorg-driver-fglrx (= 8.25.18-1) ; cependant :
  La version de xorg-driver-fglrx sur le système est 7.0.0-8.25.18+2.6.15.11-3.
```

The big problem I have is that the package is marked as broken in synaptics, so each time I want to update another package, or install a new one, it gets uninstalled, so I need to reinstall it manually....

---

