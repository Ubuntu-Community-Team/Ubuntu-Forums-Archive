---
title: "Cracking Ubuntu"
date: 2012-01-13
forum: General Help
---

### Post by Tian84 on 2012-01-13
Okay, here's my situation. I started a new job in September. The guy I replaced had to quit for medical reasons, and actually died the week I started. I have 2 computers, one runs Windows 7, one runs Ubuntu. I have not been able to crack the Ubuntu computer. No idea what version it is, don't have the original CD, can't access GRUB, what do I do? All I can think is re-download, and overwrite. I was hoping for a simpler solution.

---

### Post by oldfred on 2012-01-13
Welcome to the forums.

If you hold either tab or shift key depending on version do you get a grub menu? Or is system not booting at all? Then you may have to reinstall anyway. 

You should have a liveCD of the current version and a new version of Ubuntu. I like to also have one or more repairCDs like a gparted liveCD, Knoppix, Slax, SystemRescue, Supergrub, Boot-repair or others.

Boot repair can also run the boot info script which will document the boot process and versions installed. You can download it in an Ubuntu liveCD or download its liveCD.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by haqking on 2012-01-13
> **Tian84 said:**
> Okay, here's my situation. I started a new job in September. The guy I replaced had to quit for medical reasons, and actually died the week I started. I have 2 computers, one runs Windows 7, one runs Ubuntu. I have not been able to crack the Ubuntu computer. No idea what version it is, don't have the original CD, can't access GRUB, what do I do? All I can think is re-download, and overwrite. I was hoping for a simpler solution.

If it is your machine and you have physical access you can reset the password.

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

or use a Live CD/DVD for recovery.

If you just want the data then as long as there is no encryption then you can boot to any Linux live CD/DVD and access the data.

If things are encrypted etc then I am afraid cracking of any description is not supported here.

Cheers

---

### Post by howefield on 2012-01-13
> **Tian84 said:**
> All I can think is re-download, and overwrite. I was hoping for a simpler solution.

That's exactly what I would do, I'd want my computer to start pristine without someone elses "stuff".

Perhaps these will help :-

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)
[https://answers.launchpad.net/ubuntu/+question/42649](https://answers.launchpad.net/ubuntu/+question/42649)

---

### Post by ajgreeny on 2012-01-13
So what happens when you switch on?

Do you know how to use ubuntu if the computer could be booted successfully?

You could easily find out quite a bit about the machine's version of ubuntu and software by running a live CD/USB and navigating to the hard drive to find all the files and folders present.  You can also backup any files and folders in the /home folder of the old OS and then reinstall the system with a stable version of ubuntu (10.04-3?) and restore the old /home back.

If that all sounds difficult, come back again for more help.  It is much easier than it may seem from that description, but as you don't say if you've ever used ubuntu or linux in the past I am covering all bases.

---

### Post by Tian84 on 2012-01-13
I have a basic knowledge of it, but the whole purpose of having it is to get more familiar with it. I used it a little bit in some of the classes I took, but not much. I like to think I know enough to follow directions!!

---

### Post by Tian84 on 2012-01-13
I will probably have to start over completely. The machine is mine; I don't need the data, just need access to explore and learn the OS. It appears to boot perfectly fine; although looking at several instruction sets, I cannot access the GRUB screen (have tried esc, shift, and tab...) There is only one user on this computer, to my knowledge, and no one knows the access password.

---

### Post by grahammechanical on 2012-01-13
It seems that the best advice is to create a Live CD. Before you do a fresh install run the Try Ubuntu option and look for a program called Gparted or something, like that. It is the partition manager that will run when do install. Find out what partitions are on the machine.

There should be a minimum of two. One for the OS (called / ) and one for Swap. With a bit of luck there might be three. The previous user might have up set up a /home partition where the user configuration files and data are stored.

If this is the case then you can install the OS in the / partition by giving it a mount point of / and marking it to be formatted and then give the /home the mount point of /home but without being formatted and then the data will not be over-written. It is how we re-install without loosing data.

You might want to set up a separate /home partition for yourself if there is not one already.

This might help

[https://help.ubuntu.com/community/HowtoPartition]("https://help.ubuntu.com/community/HowtoPartition")

Regards.

---

### Post by haqking on 2012-01-13
> **Tian84 said:**
> I will probably have to start over completely. The machine is mine; I don't need the data, just need access to explore and learn the OS. It appears to boot perfectly fine; although looking at several instruction sets, I cannot access the GRUB screen (have tried esc, shift, and tab...) **There is only one user on this computer, to my knowledge, and no one knows the access password**.

The links were posted a couple of times above on how to reset the password.

Cheers

---

