---
title: "Installing Windows 7 dual boot on my Ubuntu laptop"
date: 2011-10-09
forum: General Help
---

### Post by rmcellig on 2011-10-09
I have Ubuntu 11.94 running on my Laptop and would now like to install Windows 7 so that I can dual boot in either one. What are the steps involved in installing Windows 7 on my Ubuntu laptop. I know how to install Ubuntu on a Windows machine but am not quite sure how to do it the other way around.

---

### Post by oldfred on 2011-10-09
Windows 7 normally want two partitions, one 100MB for boot/recovery. That is so you can encrypt the main install. But it installs to one partition if you create a NTFS primary (sda1 thru sda4) partition with the boot flag.

---

### Post by TeoBigusGeekus on 2011-10-09
Create an ntfs partition with a live cd and gparted and install win7 there.
Nothing to it, apart from the fact that windows will overwrite your mbr and thus grub.
[Here]("https://help.ubuntu.com/community/Grub2#ChRoot")'s how to restore it.

---

### Post by raja.genupula on 2011-10-09
First install the windows in your system, then follow these steps to recover your grub to get dual boot.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

All The Best

---

### Post by rmcellig on 2011-10-09
So all I have to do is boot from the Ubuntu live CD, create the NTFS primary partition then reboot with the Win7 CD and install it on that partition? Sounds pretty straight forward. So I will be able to select Win7 or Ubuntu on system startup in the GRUB boot loader?

---

### Post by TeoBigusGeekus on 2011-10-09
> **rmcellig said:**
> So I will be able to select Win7 or Ubuntu on system startup in the GRUB boot loader?

No. Grub will be overwritten; you have to restore/reinstall it yourself.

---

### Post by raja.genupula on 2011-10-09
> **TeoBigusGeekus said:**
> No. Grub will be overwritten; you have to restore/reinstall it yourself.

+1
to get the grub back i have given a link at post no 4.look at that.

---

### Post by viperdvman on 2011-10-09
When dual-booting **any** OS alongside Windows, I've always gone by the philosophy "Install Windows first, then your second OS". And it was and still is a good philosophy to go by since Windows likes to partition everything themselves and write their bootloader straight into the MBR.

When I did my dual-boot setup, I used GParted to set my partitions, then I loaded Windows first, and Ubuntu second. For Ubuntu, I put the GRUB bootloader in the same partition as my Ubuntu OS, and I let my Windows bootloader chainload GRUB. It's a bit more complex starting out, but it removes a lot of drama whenever a Windows Service Pack or any other major updates come out, as SP's tend to overwrite the MBR as well. Windows Vista/7, however, makes dual-booting a lot easier with EasyBCD. XP, however, you have to use *dd* to copy the first 512 bytes of your Ubuntu partition into an .img file ("bootubuntu.img" for example), and copy that to a USB/SD card... then copy that into your Windows C:/ and edit your boot.ini to point to that image file as a second OS, which then chainloads your GRUB and thus Ubuntu.

Believe me, I had an easier time using EasyBCD on my netbook (which has Windows 7 Starter) than I did going through multiple steps with my desktop (which has Windows XP). But bottom line, it's best if you install Windows first, and then Ubuntu.

---

### Post by rmcellig on 2011-10-10
Problem is that I already have Ubuntu installed on my laptop.

---

### Post by Mark Phelps on 2011-10-11
What folks are telling you is the PREFERRED sequence of installing dual-boot machines -- MS Windows first.  

But, you can still install it second.  

As indicated, you will have to reinstall GRUB because the Windows install will remove the GRUB entry from the MBR.

---

### Post by rmcellig on 2011-10-11
Thanks Mark.

Actually I was thinking  of installing a new clean copy of 11.10 on my laptop when it comes out this week. My laptop is for test purposes. This is how I learn about Linux etc... At the moment my main computer is my Intel iMac running OS X Lion. I spend about 80% of my time in Linux though because it seems to be faster and I think more to my liking. There are still a couple of apps on my Mac that I would like to find similar functionality in Linux.

It's funny because I have another test laptop (sitting next to my Linux laptop), that I run Windows 7 on. BIG difference when I show people what Linux can do compared to Windows 7.

---

