---
title: "How reliable is dual boot"
date: 2010-12-21
forum: General Help
---

### Post by specter491 on 2010-12-21
First, let me say that im a noob when it comes to linux lingo, how ever im somewhat knowledgeable when it comes to computers in general. I wanted to set up a dual boot on my laptop with Win7 and Ubuntu 10.10. Its an HP that came with windows vista and a free upgrade to W7. Its 64 bit. I have ubuntu 10.10 on a CD right now and it gives me the option to install it alongside windows (i dont want to get rid of windows, just wanna try ubuntu). My friend says i need to partition my hard drive in order to have a dual boot, is this true? Or just run the install from the CD? Does this automatically partition my hard drive? If so, how much does it use? 
     And in researching this, ive seen a number of problems people have with dual booting w7 and ubuntu. How common is this? its hard to tell because only the people that had problems are gonna post about it, not the ones that worked fine :P

---

### Post by mr.farenheit on 2010-12-21
from what i've seen your best bet is to start from scratch. a complete reformat with installing ubuntu first would work the best considering the windows installer likes to delete anything that isn't windows related. i have had with some success been able to install ubuntu by using windows disk management tool to shrink the windows partition and use the remaining free space to install ubuntu. also dual boot is fairly reliable as long as you don't make any major changes that might affect the file system integrity.

---

### Post by wilee-nilee on 2010-12-21
No reinstalls needed I'm quite sure, for a dual boot.

Take a screen shot of the gparted partitioner in Ubuntu, menu-system-admin-gparted.

In menu-accessories use the takescreen shot tool.

---

### Post by claracc on 2010-12-21
I have a hp compaq 6720s with win vista pre installed and dual boot with ubuntu lucid lynx, and I am happy with them.

Before to resize partitions or any other thing I recommend to try ubuntu from the live CD without altering any part of your installation. You boot from live CD and select the right option.

Then , if you are satisfied with ubuntu, you can resize your win partition (win tool) and install ubuntu in the way this link recommends: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot). I think that first I would upgrade to win 7.

Anycase, although my computer is also 64 bits I have installed the 32 bits ubuntu software ( It is more reliable and give less problems than 64 bits one)

---

### Post by specter491 on 2010-12-21
> **claracc said:**
> I have a hp compaq 6720s with win vista pre installed and dual boot with ubuntu lucid lynx, and I am happy with them.

Before to resize partitions or any other thing I recommend to try ubuntu from the live CD without altering any part of your installation. You boot from live CD and select the right option.

Then , if you are satisfied with ubuntu, you can resize your win partition (win tool) and install ubuntu in the way this link recommends: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot). I think that first I would upgrade to win 7.

Anycase, although my computer is also 64 bits I have installed the 32 bits ubuntu software ( It is more reliable and give less problems than 64 bits one)


The link you provided also describes partitioning the hard drive with the installation disc. This would work too right? Will it erase anything? or just set aside some space for ubuntu to use?

---

### Post by claracc on 2010-12-21
The way I made my dual boot was resizing the hard drive in win vista with its own tool and rebooting( previously you have to defrag the hard drive and rebooting too).

Then I used the live CD to install ubuntu in the resized empty partion. I had not problem messing with partitions.

I think that If you use the live CD to do the partitions, everything would be ok, but I have read some links where using resizing partition win tool is recommended.

---

### Post by theasprint on 2010-12-21
Hi,

Here, it is a simple and easy-to-understand how to dual-boot Windows and Ubuntu.

[http://ubuntuforums.org/showthread.php?t=1649050](http://ubuntuforums.org/showthread.php?t=1649050)

Good Luck :D

---

### Post by veggen on 2010-12-21
Wait, if all the OP is trying to do is try Ubuntu, how come no one suggested Wubi? They'll go through the patritioning hassle if deemed appropriate afterwards.

---

### Post by Phanes on 2010-12-21
I run windows 7 and ubuntu 10.10 on a dell laptop and it runs well. I partitioned the drives manually from the advanced option of the ubuntu installer to avoid trashing my windows 7 partition. Windows 7 was already installed and like you I didnt want to take a chance. The only issue is setting the partitions sizes for the boot, swap and main and user area but let me know if you need more info on that.

---

### Post by garvinrick4 on 2010-12-21
If you partition your drive, every partition believes it is its own drive. So it will run
perfectly if you have 5 different Operating systems. The Ubuntu's grub2 is fantastic
and will boot them all at the touch of your finger. Take advantage of the previous post
to give you personal instructions on partitioning your drive and you just install into that
partition. The guys that write this code make it pretty darn simple to install. Tis not
rocket science give it a go you will be happy you did if you get satisfaction out of learning.
There are lots of users on these forums that will help you get started. They actually have
a forum for beginners, use it that is what it is there for, you.

---

### Post by WorMzy on 2010-12-21
I currently multi-boot nine operating systems*, and I can confirm that you generally don't need to wipe your disk and start over, or install OS' in a specific order**. However, I use OEM disks to install Windows (except in the case of Vista, which originally came with my PC and I only have a recovery disk for), some Windows recovery disks may insist on reverting the hard drive to it's "factory" state.

> Wait, if all the OP is trying to do is try Ubuntu, how come no one suggested Wubi?

I agree, Wubi would be a valid option in this case. OP, you can install Ubuntu inside Windows. It's not an ideal solution, but it will allow you to try Ubuntu out without the risk of messing up your partitions. However, Wubi isn't designed as a permanent solution, so if you feel like you would like to use Ubuntu as a permanent OS, then stopping using Wubi and installing to a partition is recommended. Read more about Wubi [here]("http://www.ubuntu.com/desktop/get-ubuntu/windows-installer").



*Ubuntu 9.04, Ubuntu 10.04, Ubuntu 10.10, Debian 5.04, Arch x32 (GNOME), Arch x64 (GNOME), Arch x64 (XFCE), Windows XP, Windows Vista.

**I installed in this order (approximately) U9.04 -> Windows XP -> D5.04 -> Arch x64 (G) -> U10.04 -> Arch x32 (G) -> Windows Vista -> Arch x64 (X) -> U10.10

---

### Post by amsterdamharu on 2010-12-21
I have had one post here where the OP says he choose "install along side Windows" where the install wiped windows away and used the entire harddisk. Another user posted a comment saying that this is a bug in the Ubuntu install.
[http://ubuntuforums.org/showthread.php?t=1647243](http://ubuntuforums.org/showthread.php?t=1647243)

I don't know of this bug and not about to try if it's true but would suggest manually partitioning everything.
And update the installer before installing:
```
sudo apt-get update
sudo apt-get upgrade ubiquity
```

---

### Post by Frogs Hair on 2010-12-21
I have had no problem with my dual boot  ,  I set aside the Ubuntu space in  Windows first from  disk management  and select that partition during Ubuntu installation . I prefer a clean installation . 

Another option is setting up a data partition separate from Windows and Ubuntu . I have not tried this but it seems like a good way to protect your data from fubar , but I need to learn more about it .  If I were using LTS releases I would consider this.

As for daily use , both operating systems are used without any problem . Wubi is an option if you just want to test Ubuntu and use occasionally  . I have installed with Wubi on Win 7 nine times with friends with out any problems.

---

