---
title: "can i install windows 7 along with the currently installed ubuntu 9.10"
date: 2010-04-03
forum: General Help
---

### Post by amit.neo2000 on 2010-04-03
[SIZE=2]hey every body...):P
I am currently using ubuntu 9.10 o.s. in my P.C.

I wanna ask weather it is possible for me to install windows 7 along with my currently installed ubuntu...???
  
I know that its possible to do the reverse ( i.e. to install ubuntu in pre installed windows.)
but I am not sure about installing windows in pre installed ubuntu.

If its possible then please tell me the way to do it with the minimum data loss.
because I know that the type of disk used in windows is different from ubuntu.

should I make a separate partition for windows and then formate it while windows installation???:KS
thanks:guitar:!!!
[/SIZE]

---

### Post by manoriax on 2010-04-03
In order to install Windows, you have to ensure there's enough disc space available. You can use e.g. [GParted]("https://help.ubuntu.com/community/GParted") to create a partition for Windows.
Install Windows then (it will overwrite the boot sector of the hard disc, of course, so you won't be able to boot Ubuntu after that). Reboot from an Ubuntu live CD and re-install [Grub 2]("https://help.ubuntu.com/community/Grub2"), then. It will create a new list of the installed operating systems, so you are able to select either Ubuntu or Windows to boot.

---

### Post by amit.neo2000 on 2010-04-03
but is there any data loss in this???
and do i have to re install the ubuntu again???

---

### Post by manoriax on 2010-04-03
There is always a danger of losing data in such a process, but usually all data is safe. And no, you do not have to re-install Ubuntu after this.

---

### Post by techunit on 2010-04-03
Yes you can. It isn't as easy but it is definitely possible. There is some info on doing this here: 

[ https://help.ubuntu.com/community/WindowsDualBoot ]( https://help.ubuntu.com/community/WindowsDualBoot )

Personally I would back up my data from the ubuntu installation and install Windows 7 over the current ubuntu installation and then dual boot the system when Ubuntu 10.04 comes out at the end of April. That way you will have an up to date system and an easily dual booted system..

I believe that the windows bootloader will write over the GRUB boot loader and you will end up having to install GRUB again It is much simpler just to wait than to cause your self more headache.

---

### Post by oldfred on 2010-04-03
Just make sure windows is installed on a primary partition. You do not have to reinstall but any system change has some risk (more where we hit the wrong key and delete something we did not want to).

It is not difficult to reinstall grub2 from a live CD.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

