---
title: "recovering grub"
date: 2012-04-23
forum: General Help
---

### Post by thedoggy on 2012-04-23
Hi guys, i know its a common problem and theres is tonnes of info, but i just cant get it to work.

Its the usual problem, after reinstalling windows my grub boot loader got wiped from the MBR.
Ive tried all the instructions to reinstall/recover (by booting from the live ubuntu), and i always end up at some grub rescue screen (clearly something went wrong).

Can someone please walk me through it so i get every single line of code correct, specific to my computer.

Thanks.

---

### Post by gshreya3 on 2012-04-23
Please visit 
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by westie457 on 2012-04-23
Welcome to UF.

The information you require is here.
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by thedoggy on 2012-04-23
> **gshreya3 said:**
> Please visit 
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)


I tried these ones last night but ended up in grub rescue.

---

### Post by thedoggy on 2012-04-23
> **westie457 said:**
> Welcome to UF.

The information you require is here.
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

Ill read through this. maybe it will tel me what i was doing wrong. Thanks.

---

### Post by thedoggy on 2012-04-23
ive already got a problem. when i try run the bootinfo script, it says no such file or directory.

ill ignore that and move on lol.

---

### Post by thedoggy on 2012-04-23
ubuntu@ubuntu:~$ sudo chroot /mnt 
chroot: failed to run command `/bin/bash': Exec format error



i cbf anymore. quicker to just reinstall.

---

