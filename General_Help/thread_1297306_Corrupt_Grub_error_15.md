---
title: "Corrupt Grub error 15"
date: 2009-10-21
forum: General Help
---

### Post by tongoll on 2009-10-21
i know there are threads about this all ready, but my problem... is a bit messed up and i cant understand it from reading any of the other ones.

i deleted the partitions that i had installed the latest ubuntu on, i had installed the 64 bit by mistake and needed to downgrade to 32. 

anyways, so i deleted the partitions, but the old grub is still active but deleted... if that makes sense.

it should have been whipped out along with the partition right? but it wasn't...and when i try to re install it, the grub isn't being detected at all, its like its there but not detectable.... 

i have as right now, the following partitions

/dev/sda1
/dev/sda5
/dev/sda6
/dev/sda3

5 is the linux ubuntu 9.4 32 bit, sda 6 is the swap, 3 is my vista reformatter, 1 is vista.


*im going off the top of my head right now my lapppy overheated but after typing them so many times i am pretty sure thats about right, i know for a fact the linux partitions are*
-----------------------THE JIST-----------------------------
i had installed the 64 bit version realized the mistake and couldn't uninstall *vista is taking a dump right now does not wana work.* so i installed 32 bit version on another partition tryd to log on and it kept running the 64 bit version so i deleted both partitions and tryd to install it all over but now it just gives me loading  error 15
it cannot locate any grub neither through "find /boot/grub/"i tryd every partition and stage 1" or by "find /grub/"same as before"

so i can not locate where it would be to even re install it...

---

### Post by speed32219 on 2009-10-21
Posted earlier by COMPILEDKERNEL.

 Re: Help restoring Ubuntu Grub/Boot Partition

[http://gwos.org/udsf/doku.php/core:grub:restore](http://gwos.org/udsf/doku.php/core:grub:restore)

---

### Post by tongoll on 2009-10-21
i did everything on the page it said to do but now i face a new problem....

the grub sends me to a interface... i don't know how to explain it....
it says


[minimal BASH-like line editing is supported. for the first word, TAB list possible command completions. anywhere else TAB lists the possible completions of a device/filename.]it wont give me a option to bot to linux or anything just straight to that terminal

---

### Post by tongoll on 2009-10-22
bump  :(

---

### Post by mechro on 2009-10-22
If you deleted partitions then Ubuntu has been deleted and you can't then say "5 is the linux ubuntu 9.4 32 bit" unless you had two Ubuntu installations.

Part of Grub is in the Master Boot Record and is not necessarily deleted when you delete a partition. The Grub in the MBR is looking for an installation which doesn't exist.

You now have to decide what you want to achieve in the way of restoring or re-installing one or more operating systems.

Edit: My bad. I've now read "the Jist". I'll have a ponder.

---

### Post by mechro on 2009-10-22
Is this any easier?...

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Restoring GRUB](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Restoring GRUB) > Restoring Grub

---

