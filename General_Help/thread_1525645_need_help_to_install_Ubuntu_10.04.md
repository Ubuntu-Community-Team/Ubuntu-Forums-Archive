---
title: "need help to install Ubuntu 10.04"
date: 2010-07-07
forum: General Help
---

### Post by KCMO on 2010-07-07
I have a Toshiba Satellite A135-S4476. It came with windows vista and one of my friends installed PCLinuxOS. So it has dual boot. I want to replace PCLinuxOS with Ubuntu 10.04 netbook edition. I do not know how to do that. Kindly help me. I am not a computer expert so kindly give me detail instruction. 

By the way do I need the netbook  version for my laptop or I can install the desktop version in my laptop.

I really appreciate your help.

Thanks,

---

### Post by TheWeakSleep on 2010-07-07
I am kind of confused, do you want to continue dual-booting with ubuntu and vista instead of pclinuxos and vista?

and yes, you can use the full version, you do not need the netbook edition :)

---

### Post by mikewhatever on 2010-07-07
Here is the link for installation instructions [-->link<--]("https://help.ubuntu.com/10.04/installation-guide/i386/installation-howto.html"), and more [-->link<--]("https://help.ubuntu.com/10.04/installation-guide/i386/index.html").
You can use any version you want, although, the desktop one is recommended for a standard 15" laptop.

---

### Post by David Batty on 2010-07-07
A noob method to do this would be to remove the linux partitions through vista using one of the free download partitioning managers.
When you reboot you will get the blue screen of death because you have removed the grub bootloader. 
Dont panic insert your linux cd/dvd and follow the instructions to install whatever flavor of linux you desire as a dual boot.
BEWARE make sure everything is backed up beforehand, the linux cd works and you have a Vista restore disc just in case. Defrag your vista disc beforehand is a wise option too.
Good luck.

---

### Post by KCMO on 2010-07-07
Yes, I want to continue dual booting using vista and ubuntu instead of vista and pclinuxos.

I will appreciate if somebody provides name of any specific partitioning manager that works. Also is there an instruction regarding how to partition a hard disk?

I do not know much about computer.

---

### Post by David Batty on 2010-07-08
Google partition manager and you will see there are several free partition managers offered. Vista also has one built in I'm told. Download one and try it out it and see if it detect your partitions. 
Your windows partitions are usually NTFS. linux ones are often ext3, or ext4. You should be able to identify which ones you want to keep quite easily.
If this is too hard then consider adding a third operating system, and leaving the other two there. This is real easy to do if there is plenty of space on your hard drive. Have a look at the free space space in each of your two operating systems and decide where you will poach the space from or just leave the Ubuntu installer to decide that for you.
Once you have three systems running you can transfer any files across to Ubuntu without have to restore from your backups. The only downside is that your grub boot options will be a little more confusing with all the choices.

---

### Post by mikewhatever on 2010-07-08
> **KCMO said:**
> Yes, I want to continue dual booting using vista and ubuntu instead of vista and pclinuxos.

I will appreciate if somebody provides name of any specific partitioning manager that works. Also is there an instruction regarding how to partition a hard disk?

I do not know much about computer.

The partition manager to use is Gparted. It should be under System->Admin on th Ubuntu live cd. 
Since you want to replace PCLinux with Ubuntu, there is no need to repartition. Launch Gparted and delete the PCLinux partition, then, close Gparted and click the 'Install Ubuntu' icon on the desktop. At the partitioning stage, select the following option: 'Use the largest continuous space'.
Please note that deleting a partition will erase all its data. Make sure you back up the files you need before doing it.

---

