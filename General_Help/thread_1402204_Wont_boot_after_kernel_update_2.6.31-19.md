---
title: "Wont boot after kernel update 2.6.31-19"
date: 2010-02-08
forum: General Help
---

### Post by wigglestix on 2010-02-08
I updated my kernel yesterday and now when i boot up my laptop none of the kernels will boot.  When i try to boot off the latest kernel or any kernel for that matter it just stops and goes blank. Tho only think i could think of is to use the command line in the grub but the commands are very limited. Any help is greatly appreciated.

Please help!

---

### Post by Bryan.Smith on 2010-02-08
I am having exactly the same problem with "Ubuntu, Linux 2.6.31-19-generic".  I assume that it is a major problem with the new kernal or files associated with the new kernal.

I am using Ubuntu not kubuntu.   I can boot into Ubuntu using the live CD which suggests there is no hardware fault.

When I reboot from the hard disk I see the following on the my screen.

Launch operation system ...
Boot from CD/DVD
Grub loading.

The ubuntu icon consisting of three segments and three circles then appears for a few seconds.

I then see some text appear momentarily on the screen (a fraction of a second).

Then all activity on the hard disk appears to cease.

---

### Post by wigglestix on 2010-02-09
Yes this sounds like the exact same problem i am having. So far i have done some reaserch and alot of people are having this problem with this kernel update. From what ive read there dose not seem to be a fix for this yet but i assume eventually someone will figure it out.

---

### Post by ngrieb on 2010-02-09
I found a temp fix for this by editing the grub boot, switch the uuid to /dev/sdXY, and it will allow you to boot at least a few times. See: [http://ubuntuforums.org/showthread.php?t=1400783](http://ubuntuforums.org/showthread.php?t=1400783)

The text you are referring to seems to be a Firestarter message on my computer, I think Firestarter not correctly killing itself and is perhaps not allowing the correct unmounting of the HD upon shutdown...?

---

### Post by wigglestix on 2010-02-09
> **ngrieb said:**
> I found a temp fix for this by editing the grub boot, switch the uuid to /dev/sdXY, and it will allow you to boot at least a few times. See: [http://ubuntuforums.org/showthread.php?t=1400783](http://ubuntuforums.org/showthread.php?t=1400783)

The text you are referring to seems to be a Firestarter message on my computer, I think Firestarter not correctly killing itself and is perhaps not allowing the correct unmounting of the HD upon shutdown...?


Ive tried this and it dosent seem to be working, ive tried all the partitions i could think of alltoough i prety sure its installed on sda5. I have also tried using older kernel versions with this configuration and its just isnt working.

My drive is partitioned in halfs 115gb for ubuntu and 115gb for vista. I installed ubuntu 9.10 via wubi quite some time ago and havent had any problems with kernel updates prior to this. I hope this extra info helps.

---

