---
title: "Dual Booting With Two DIfferent Linux Systems"
date: 2010-07-13
forum: General Help
---

### Post by giddyup306 on 2010-07-13
Hello.  First, I'd like to say that I did several searches, and haven't been able to yield one result.  The terms are too generic, and the closest thing I can find is dual booting with Mac and Windows, not Linux and Linux.  I'm sure this topic has been posted one million billion times, and I'm sure it's been beaten to death.  Anyways there is a guy in the Community Cafe forum that wants people to test his remix of Ubuntu. I want to give him/her an accurate opinion, so running it in a virtual machine just won't cut it.  I don't have an extra computer, and I have way too much tweaking to delete the stuff off of my computer.  

So if you could point me in the right direction I'd appreciate it.  I thought that I could type in "dual boot -mac -windows", and it doesn't eliminate the mac or windows words.  So I guess I could use some tips on searching as well (even tho a while ago I thought I read something on searching tips).

---

### Post by Naitsirhc Hsem on 2010-07-13
Install in another partition and grub should automatically be updated during the install :)

---

### Post by giddyup306 on 2010-07-13
> **Naitsirhc Hsem said:**
> Install in another partition and grub should automatically be updated during the install :)
Thanks for the reply.  Is there an easier way to create a partition than using Gparted?  Back when I had Windows and Ubuntu on my machine I tried to resize my Ubuntu partition (I only originally allocated something like 10GB to try it).  Somehow the program locked up right in the middle of the repartitioning process, and I lost both operating systems.  No I didn't create a backup either like I should have. I might have to use remastersys to make a backup, but I haven't had much luck with that.  Then again I only tried to make distro copies.

---

### Post by WorMzy on 2010-07-13
You can have as many different Linux installations as you want, so long as your hard drive(s) has space for them all. Just bear in mind that you can (usually) only have four primary partitions on a single hard drive, so make sure that at least one of them is an extended partition which stretches as far as it can. An extended partition is a primary partition which acts as a shell to contain other partitions in, allowing you to circumvent the four partition limit. You need to have at least one other primary partition on your disk(s) as well as an extended partition, as the MBR on partitions contained in an extended partition can't be read by most BIOS', so you need another primary partition to install stage1 of Grub to.

Unfortunately, messing about with partitions will always run the risk of borking all your OS', regardless of which partition editing software you use. If you don't want to run the risk of losing everything then back it all up, or stick with the OS' you have now.

---

### Post by Megaptera on 2010-07-13
This guy multi-boots 145 or so linux distros, a bit more than most of us but some useful principles and advice:

[http://www.justlinux.com/forum/showthread.php?p=861282#post861282](http://www.justlinux.com/forum/showthread.php?p=861282#post861282)

Hope it's of interest?

---

### Post by 3Miro on 2010-07-13
I have dual boot of Ubuntu and Xubuntu. For all intensive purposes the whole process works just the same as in dual booth windows/linux with only couple of minor details.

1. The different Linux versions can share common swap partition. The only issue there might be if you are using a hibernate option from one distro and the boot into another.

2. Depending on the distros that you are using you may run into grub 1 vs grub 2 issues. I had some trouble making Fedora work with Ubuntu due to that. You have to either install Ubuntu second (with grub 2) or not install Fedora's bootloader and then update Ubuntu's grub 2 manually.

3. When a new version of the kernel comes out, you will have to update all the distros to detect all the new options, or manually update grub.

---

### Post by giddyup306 on 2010-07-13
> **WorMzy said:**
> 
Unfortunately, messing about with partitions will always run the risk of borking all your OS', regardless of which partition editing software you use. If you don't want to run the risk of losing everything then back it all up, or stick with the OS' you have now.
Yeah I guess I'll just have to make a copy before I try.  I do have a clone on an external drive now, but it doesn't like to mount easy.

> **Megaptera said:**
> This guy multi-boots 145 or so linux distros, a  bit more than most of us but some useful principles and advice:

[http://www.justlinux.com/forum/showthread.php?p=861282#post861282](http://www.justlinux.com/forum/showthread.php?p=861282#post861282)

Hope it's of interest?
And I thought the 12 or so guest operating systems were overkill.  It's cool to read, but I couldn't follow his instructions. 

> **3Miro said:**
> I have dual boot of Ubuntu and Xubuntu. For all  intensive purposes the whole process works just the same as in dual  booth windows/linux with only couple of minor details.

1. The different Linux versions can share common swap partition. The  only issue there might be if you are using a hibernate option from one  distro and the boot into another.

2. Depending on the distros that you are using you may run into grub 1  vs grub 2 issues. I had some trouble making Fedora work with Ubuntu due  to that. You have to either install Ubuntu second (with grub 2) or not  install Fedora's bootloader and then update Ubuntu's grub 2 manually.

3. When a new version of the kernel comes out, you will have to update  all the distros to detect all the new options, or manually update  grub.

Oh they are both Ubuntu 10.04.  The only thing that may or may not be a problem is that the one I want to try is a 64 Bit version.  I don't even know if my ancient computer can handle it.  I'll run it in a virtual machine first. 

You said that it works like windows/linux but I don't understand how the install is the same.  When you install Ubuntu on windows, the CD runs and you can you make the partition right there.  I'm still confused as to how this will work.  

I did find a how-to on Ubuntu and Fedora, but I'm not sure what differences there will be with Ubuntu to Ubuntu.

[http://gwos.org/udsf/doku.php/core:dualbooting:ubuntu](http://gwos.org/udsf/doku.php/core:dualbooting:ubuntu)

---

### Post by nothingspecial on 2010-07-13
If you are going to do this you may want to consider using a seperate home partition.

I have 2 7gig partitions on this computer, one has normal ubuntu on it (for the family) and one has a very personalised ubuntu minimal install on it for me. But they both use the other huge partition as /home. So that any applications that are installed on both systems have the same settings and all your stuff is in the same place.

---

