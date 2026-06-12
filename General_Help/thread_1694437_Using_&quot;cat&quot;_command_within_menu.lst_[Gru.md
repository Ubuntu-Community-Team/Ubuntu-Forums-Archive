---
title: "Using &quot;cat&quot; command within menu.lst [Grub4DOS]"
date: 2011-02-24
forum: General Help
---

### Post by Kwax on 2011-02-24
Hi everybody,

First of all, I'm far from beeing a Linux or any other OS expert, so excuse me if my questions are dumb ;)

I use grub4Dos to boot on an USB stick and launch various windows tools/installers.

The problem here is that windows 7 and vista installers both use a 'BOOT' folder containing the boot config files. (dcb, boot.sdi and some other stuff)
Of course I can't have 2 folders with the same name at the same place (here the root of my usb stick).


So here is what I d'like to do :

I saw ( here [ http://diddy.boot-land.net/grub4dos/files/commands.htm#cat]("http://diddy.boot-land.net/grub4dos/files/commands.htm#cat") )
that grub allows the use of the cat command, which should allow me to change the content of the files in the 'BOOT' folder before chainloading any install.

Unfortunately I can't find a way of doing so.

Here is what I tried :

```
title Install Windows 7
root (hd0,0)
cat (hd0,0)/WIN7/dcb > (hd0,0)/BOOT/dcb
cat (hd0,0)/WIN7/boot.sdi > (hd0,0)/BOOT/boot.sdi
chainloader (hd0,0)/bootmgr
```when I boot on my usb stick and try to launch the entry 'Install Windows 7' the cat command fails to find the files.

So if anybody has any Idea on how to solve this I would appretiate it greatly ;)

Thanks

PS : English is not my native language so excuse me for the spelling and grammare error I could have done.

---

### Post by psusi on 2011-02-24
Grub does not support IO redirection, or any method of writing to the disk.  Windows having other files in /boot should not be a problem.

---

### Post by Kwax on 2011-02-24
Thanks for the straight answer.

I already looked into a way of modifying the boot manager of windows and the files in /boot.

When I chainload the bootmgr in the entry of menu.lst it always looks for a file named bcd placed in /boot (which has to be on the root).

This bcd file countains a serie of entries (like in menu.lst) that allow you to boot multiple OS or installs using the windows boot manger.

So I could launch the windows manager with on entry of menu.lst and then through this second menu select which os or install I d'like to boot.

But as I am a stuborn person who likes to do things the hard way, I wan't to  avoid this second menu and have instead multiple entries in menu.lst (one for each OS or install to boot).
To do so I would need to be able to call different bsd files. The problem is that I can't edit (even with an hexadecimal editor) 'bootmgr' and modify the name of the bsd file it uses.

Anyway, I just realise that it has pretty much nothing to do anymore with grub, so I'll try to find more about the windows boot manager.

Thanks for the help.

---

