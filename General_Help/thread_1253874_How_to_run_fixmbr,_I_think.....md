---
title: "How to run fixmbr, I think...."
date: 2009-08-30
forum: General Help
---

### Post by jschille on 2009-08-30
So, I am reinstalling Ubuntu because I did I terrible job with my partitions the first time.
I went into Vista and deleted the Ubuntu partitions and then made a new partition to install Ubuntu on.
I read somewhere that before I install Ubutunu I need to run fixmbr from the command line.
I put my Windows Vista (dell disk) in my comp started the cmd promt and can't figure out how to run fixmbr.
Do I need to run fixmbr or can I just start my new installation of ubutunu?
Thanks!

---

### Post by Liolikas on 2009-08-30
I never messed in this way but I do not think that fixmbr is important. it may be important when you remove Ubuntu and end up with no windows too. Just type that command into cmd it will nuke GRUB and install windows thing ntldr instead of it. And ntldr is bad for you because it is unable to start other os, only windows. Grub starts all things you know and even more.

---

### Post by vttay03 on 2009-08-30
You should be able to just run the Ubuntu install and Grub will automatically detect Vista.  After the Ubuntu install is over, the Grub boot menu will ask on startup which operating system you'd like to run.  You'd only need to run fixmbr if you were trying to fully restore to Vista without Ubuntu at all.

---

### Post by lisati on 2009-08-30
You probably don't need to worry about fixmbr unless you are restoring your system to "Windows Only" for some reason (as I will be later before taking my laptop in for repairs to the keyboard)

---

### Post by mike555 on 2009-08-30
did you do a wubi install? or are you doing a real install?  if you did a real install you wouldn't need to delete Ubuntu from vista, just reinstall Ubuntu to the partition it was on or whatever partition you made , it will install grub and let you pick Windows or Ubuntu .. ( of course pick the MANUAL install from the installer and be sure you pick the right partition , so you don't delete Windows)

---

