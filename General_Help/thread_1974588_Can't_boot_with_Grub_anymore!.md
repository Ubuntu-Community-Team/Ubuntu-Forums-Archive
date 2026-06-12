---
title: "Can't boot with Grub anymore!"
date: 2012-05-06
forum: General Help
---

### Post by n17182559 on 2012-05-06
Hello,

I am writing this thread from Windows 7 because I have a problem with ubuntu (or with booting ubuntu.) Please note that I am not yet very good with Linux, still  learning!

I used to boot with Grub and choose between ubuntu or Windows, and I was happy with that. However, I accidentally booted my Windows recovery partition. I cancelled as soon as it asked me anything, but as I restarted my computer (over and over again), Grub kept showing an error and I could only enter some commands.

Since I didn't know what to do, I booted from a ubuntu 11.10 live CD and used Boot-Repair as shown in [this tutorial]("https://help.ubuntu.com/community/Boot-Repair").

Now, my computer automatically boots Windows 7. You might understand why if you look at this [Boot-Repair report]("http://paste.ubuntu.com/971451/").

When I look at my partitions from Windows (or from gparted on a live CD), there is free space exactly where my ubuntu partition used to be. I know my ubuntu files aren't deleted because I can browse through them if I use [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk") from a live CD. It seems like my ubuntu partition is now invisible, marked as deleted, and I wish I could bring it back to how it was before.

I know I could make terrible mistakes if I start playing with my partitions on my own because I am very clumsy and not experimented with the whole thing, this is why I ask for advice. 

Can anybody help me?

Thanks!

---

### Post by itagomo on 2012-05-06
Yeow! I have not-totally-the-exact same problem .. my ubuntu grub was replaced by Win BootLoader after installing Win XP ..

from LiveCD, have you tried entering this command from Terminal:

**sudo fdisk -l**

it'll show up available partitions on your drive like this:

[B]   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18725   150403072   83  Linux
/dev/sda2           18725       19458     5884929    5  Extended
/dev/sda5           18725       19458     5884928   82  Linux swap / Solaris[/B]

try to mount to one of the partitions first to see if it's your Ubuntu partition, say /dev/sda1

**sudo mount sudo mount /dev/sda1 /mnt/**

this will mount /dev/sda1 to your liveCD /mnt/ folder
then

[B]cd /mnt/
ls -l[/B]

it'll display your root / folders

if it did, then continue to mount important system files

**for i in /dev/ /dev/pts/ /proc/ /sys/; do sudo mount -B $i /mnt$i; done**

and login as root to you Ubuntu distro

**sudo chroot /mnt/**

update your grub

[B]update-grub
grub-install /dev/sda1
grub-install --recheck /dev/sda1
exit (or press ctrl + D)
for i in /sys/ /proc/ /dev/pts/ /dev/; do sudo umount /mnt$i; done
sudo umount /mnt/
[/B]

restart afterwards ..

---

### Post by itagomo on 2012-05-06
[https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2)

---

### Post by oldfred on 2012-05-06
One of the first things the recovery disk seems to do is rewrite the partition table and erase Linux partitions. 

To get the suggestions above on reinstalling grub2's boot loader to work you have to use testdisk and change the d to bring back the Linux partition.

repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by n17182559 on 2012-05-07
To all those having the same problem: it worked!
Thanks!

I just "undeleted" my partition using TestDisk on a live CD. Then, I rebooted using Grub on a usb device (because my computer still didn't automatically boot on grub as before) and asked it to detect any OS: I was able to boot my good old ubuntu. I just "sudo dpkg-reconfigure grub-pc" and the problem was solved.

Thank you again!

---

