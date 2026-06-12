---
title: "MBR ate my GRUB"
date: 2010-12-13
forum: General Help
---

### Post by adduds on 2010-12-13
I know it's been asked a million times and theres been a million answers....but they all seem to differ....

Just got my comp up and running again to using Ubuntu 10.10....after couple days thought i might as
well partition and put XP on the other half....MBR wrote over GRUB what do i do once i get into console??? 

I've got windows and ubuntu on different partitions so this changes the commands too i believe

Thanks in advance

---

### Post by ChuckyDuckster on 2010-12-13
There is a program called EasyBCD for Windows that will configure your Windows bootloader. You can add Linux from there if you want to use the Windows loader. If you want to use GRUB, you will need a live CD to reinstall it

---

### Post by Rubi1200 on 2010-12-13
Hi,
if you installed XP after Ubuntu then GRUB is gone, written over by the Windows bootloader.

The fix is to reinstall GRUB and have the option to boot both operating systems.

We need to know which partition Ubuntu is installed on to give you the right commands.

Thanks.

---

### Post by dabl on 2010-12-13
Reinstall Grub, with --root-directory=/dev/sda2 (or whatever the right partition is).

[http://kubuntuforums.net/forums/index.php?topic=3106368.0](http://kubuntuforums.net/forums/index.php?topic=3106368.0)

---

### Post by adduds on 2010-12-13
> **Rubi1200 said:**
> Hi,
if you installed XP after Ubuntu then GRUB is gone, written over by the Windows bootloader.

The fix is to reinstall GRUB and have the option to boot both operating systems.

We need to know which partition Ubuntu is installed on to give you the right commands.

Thanks.

*EDIT*


ubuntu@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
aufs                 1005M   54M  951M   6% /
none                  998M  296K  998M   1% /dev
/dev/sr1              695M  695M     0 100% /cdrom
/dev/loop0            657M  657M     0 100% /rofs
none                 1005M  112K 1005M   1% /dev/shm
tmpfs                1005M   32K 1005M   1% /tmp
none                 1005M   88K 1005M   1% /var/run
none                 1005M  4.0K 1005M   1% /var/lock
/dev/sdb5              92G  3.7G   84G   5% /media/1e4c3dc0-2e96-44d2-beb4-fcec826014cc

---

### Post by adduds on 2010-12-13
> **ChuckyDuckster said:**
> There is a program called EasyBCD for Windows that will configure your Windows bootloader. You can add Linux from there if you want to use the Windows loader. If you want to use GRUB, you will need a live CD to reinstall it

I'm on a live cd right now and don't know what to do lol;)

---

### Post by wilee-nilee on 2010-12-13
So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the # in the reply panel this makes code tags  paste all the text in between.

Not much easybcd support here as it isn't needed most of the time except to fight paranoia.

---

### Post by lindsay7 on 2010-12-13
Read this, it should fix your problem,


[http://www.webupd8.org/2009/12/how-to-recover-grub2-linux.html](http://www.webupd8.org/2009/12/how-to-recover-grub2-linux.html)

---

### Post by adduds on 2010-12-13
> **lindsay7 said:**
> Read this, it should fix your problem,


[http://www.webupd8.org/2009/12/how-to-recover-grub2-linux.html](http://www.webupd8.org/2009/12/how-to-recover-grub2-linux.html)

YOU DID IT! <3

rather the link did but omg ty i wasn't sure if i was grub 1 or 2 either!

I really must thank you :)

---

