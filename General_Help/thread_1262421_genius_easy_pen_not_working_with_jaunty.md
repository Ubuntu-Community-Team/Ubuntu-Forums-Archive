---
title: "genius easy pen not working with jaunty"
date: 2009-09-09
forum: General Help
---

### Post by brabender on 2009-09-09
My small, old and trusty serial tablet, Genius Easy pen, has been working beyond expectations for many years across Windows 98, XP, Ubuntu Hardy and Intrepid, in the last two cases with precious help from this thread in the french forums: [http://forum.ubuntu-fr.org/viewtopic.php?id=222211](http://forum.ubuntu-fr.org/viewtopic.php?id=222211). Recently I upgraded to Jaunty and noticed, as usual when upgrading Ubuntu, that it does not work. Ok, time to edit again X11.xorg.conf; only this time the process fails:

antonio@sobremesa:~$ sudo apt-get install xserver-xorg-input-summa gpm
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
El paquete xserver-xorg-input-summa no está disponible, pero algún otro paquete hace referencia
a él. Esto puede significar que el paquete falta, está obsoleto o sólo se
encuentra disponible desde alguna otra fuente
E: El paquete xserver-xorg-input-summa no tiene candidato para su instalación

In english: the package xserver-xorg-input-summa is not available, but some other package it's referencing it. This maybe means that the package is missing, it's obsolete or it's only available from some other source
E: The package xserver-xorg-input-summa has no candidate for it's installation

Surely, this is related to the changes in the way X11 keeps config data; Does somebody nows if there is some way to keep using my tablet? Thank you all, and excuse my poor english.

---

### Post by Favux on 2009-09-09
Hi brabender,

I'm sure you checked in Synaptic Package Manager and didn't see xserver-xorg-input-summa.  I checked the Jaunty Packages search page and it isn't there.  It is present for Intrepid.  Then I found:  [https://launchpad.net/ubuntu/+source/xserver-xorg-input-summa](https://launchpad.net/ubuntu/+source/xserver-xorg-input-summa)  It seems to be saying summa is now unmaintained upstream of Ubuntu (Xorg?) and won't build against Xserver 1.6, which is what Jaunty has.

Do you know where the source code for the summa driver was maintained?  Someone may have figured out how to build it to Xserver 1.6.  It's also possible that another driver may work since many tablets are rebranded.

To find out what the underlying tablet is (hopefully something other than Summa?) see practic's post #11 here:  [http://ubuntuforums.org/showthread.php?t=1151464&page=2](http://ubuntuforums.org/showthread.php?t=1151464&page=2)  And the wizardpen wiki has some more on this:  [https://help.ubuntu.com/community/TabletSetupWizardpen](https://help.ubuntu.com/community/TabletSetupWizardpen)

In Jaunty you are "suppose" to use a .fdi rather than the xorg.conf.

I hope this is helpful.

---

### Post by brabender on 2009-09-10
Thanks for your answer, Favux. I think that the main problem is that it's a serial tablet, i.e., it connects to the RS232 port, not USB. Yes, it's THAT old. I guess I should invest in a new one, it's just that I hate to leave aside a bit of hardware that stills works properly after many years. Anyway, I'll keep on trying.

---

### Post by Favux on 2009-09-10
Hi brabender,

It looks like Intrepid is the last version of Ubuntu that will support it.  At the Debian package site:  [http://packages.debian.org/lenny/xserver-xorg-input-summa](http://packages.debian.org/lenny/xserver-xorg-input-summa)  there is a version for lenny.  Other than possibly at this Arch site:  [http://www.archlinux.org/packages/extra/i686/xf86-input-summa/](http://www.archlinux.org/packages/extra/i686/xf86-input-summa/)  I don't see any evidence of newer builds, ie against Xserver 1.6.  And according to this opensolaris site the summa driver was removed upstream by Xorg:  [http://bugs.opensolaris.org/bugdatabase/view_bug.do?bug_id=6826940](http://bugs.opensolaris.org/bugdatabase/view_bug.do?bug_id=6826940)  So rather than unmaintained it's been actually dropped.

News does not look good for newer versions.  Good luck!

---

