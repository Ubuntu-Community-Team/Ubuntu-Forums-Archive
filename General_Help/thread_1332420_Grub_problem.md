---
title: "Grub problem"
date: 2009-11-20
forum: General Help
---

### Post by jdjenkins on 2009-11-20
Grub version 1.97 beta 4:

I've messed something up while trying to change the boot order in the menu. Now when I select "Ubuntu" in the menu, it can't find Wubi, and just leaves me with a "grub>" prompt.

I think I need to change it to look at (hd0,2), as it is trying up to (hd0,1) at present when looking for Wubi. I'm hoping that I don't have to reinstall Ubuntu, as there's a bunch of stuff on there that I could do with copying (I know - I was just about to do a backup, honest!!).

So, is there a way to boot up Ubuntu (9.10 by the way), or somehow edit the Grub settings in the command line or even in Windows (I have XP SP3),

thanks in advance,

Jon.

ps - just tried this:

cat /grub/grub.cfg

at the grub prompt; the response is "file not found" - is this relevant for Wubi?

I still need some help on how to proceed!

---

### Post by jdjenkins on 2009-11-20
Doing some more checking - on a Live CD using the Terminal, the output of

ls /boot/grub

is

device.map    grubenv

- I should think there should be some more Grub files possibly. Any ideas?

thanks,

Jon.

---

### Post by miked2 on 2009-11-20
There's a how to [__here__]("http://ubuntuforums.org/showthread.php?t=224351") that goes through reinstalling grub from an installation cd. 

There's also some community documentation:

[https://help.ubuntu.com/community/GrubHowto]("https://help.ubuntu.com/community/GrubHowto")

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

I'm no grub expert, but just fixed my missing boot options window after reading these.

---

### Post by drs305 on 2009-11-20
jdjenkins,

I am not well versed in wubi and grub 2. From the grub 2 menu, if you get it, you can drop to the command line by pressing "c". At that point, you can use combinations of the "ls" command to see where the Ubuntu installation is.  

The community doc details how to use the grub command line, if the command line is available to you:

[https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode]("https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode")

---

### Post by jdjenkins on 2009-11-21
Thanks guys - those links are v useful. I've already had a go using the Live CD to mount the virtual drive and look at the directories.

Just one quick question - I'm trying to copy some files using the Terminal with the Live CD system, but struggling to find the command which lets me copy a whole folder/directory.

I've tried

cp /vdisk/home/mydirectory/ /media/myusbdrive

but it keeps ignoring the directory, and only copies single files when I specify them.
Looking at ss64.com/bash/cp.html, would I use cp -R to do it, or is there something better?

thanks again:),

Jon.

---

### Post by drs305 on 2009-11-21
> **jdjenkins said:**
> but it keeps ignoring the directory, and only copies single files when I specify them.
Looking at ss64.com/bash/cp.html, would I use cp -R to do it, or is there something better?

Yes, the -R switch is what you want to use. To learn about the possible options available for a command, in a terminal type "man" and the command to display a help page. These are called the "man pages" and you can find copies of them online as well.

Example:
```

man cp

```
will tell you that the -R or -r option will copy files recursively. The -p switch would also keep the ownership and timestamps the same; etc.

---

### Post by jdjenkins on 2009-11-21
Great - will give it a try in a bit,

Jon.



> **drs305 said:**
> Yes, the -R switch is what you want to use. To learn about the possible options available for a command, in a terminal type "man" and the command to display a help page. These are called the "man pages" and you can find copies of them online as well.

Example:
```

man cp

```
will tell you that the -R or -r option will copy files recursively. The -p switch would also keep the ownership and timestamps the same; etc.

---

