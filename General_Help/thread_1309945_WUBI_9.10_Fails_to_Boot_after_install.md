---
title: "WUBI 9.10 Fails to Boot after install"
date: 2009-11-01
forum: General Help
---

### Post by blizbiggy on 2009-11-01
Title says it all... It just boots to the grub command line

---

### Post by garvinrick4 on 2009-11-01
Treat it like an App in windows. You will find it located in C: in a Folder next to Users

Load thru WUBI tell what password is, tell how big you want Ubuntu. At least 10 gig.
It will come in/dev/loop0 Host will always be your Windows partition.

You can copy Windows files into your Ubuntu but not Ubuntu files into Windows.
Will be in computer/filesystem/host/user/your user name

If you want to put some linux files into Windows, copy to external and then into Windows.

fsck every so often to make sure you are clean. 

Any trouble fsck in root will usually fix problem. 

If you are 64 bit capable and you have 32 bit Windows, you can still use 64 bit Ubuntu.

Maintain your Machine. Maintain your Machine. Maintain your Machine.

If you mess it up, you can just uninstall in your Windows side and reinstall from disk
takes 12 minutes to install. Nice to keep a .iso burned image on cd of version you want handy. 

Uses grubdos4 from Windows to boot. Does not use Linux Grub2 or Grub legacy.

---

### Post by blizbiggy on 2009-11-01
This does not really fix my issue... I installed ubuntu with wubi (30gb hdd disk space) and after it finished installing and I rebooted to load up ubuntu, it just loads to the grub command line.  I have not had this issue in the past with wubi so it is new to me.  I will reboot to see what the error is and post it.

---

### Post by blizbiggy on 2009-11-01
[IMG]http://www.tfaproject.org/download/pics/junk/downsize.jpg[/IMG]

---

### Post by garvinrick4 on 2009-11-01
Sorry I have never seen that before. I have uninstalled and reloaded quite a few times
bug testing Alpha's and such. Never had a problem. Went to Windows put in CD waited
a few minutes in Window destop up pops do you want to install with WUBI takes about
12 minutes to install.  Wish I had an answer for you. Good luck.

---

### Post by blizbiggy on 2009-11-01
Well, I installed wubi and got ubuntu to install and run perfectly on my laptop... the only difference is the hardware that I am using.  My desktop is an i7 920, 6gb ddr3, 1TB WD Black, 4870x2 graphics

Both my desktop and laptop use Windows 7 x64 Professional

IDK I am lost on this one LOL

---

### Post by hezuo on 2009-11-02
I'm having the same problem. does anyone have any clue on how to solve this? please help.

---

### Post by blizbiggy on 2009-11-02
I tried last night installing it on my other hard drive just to be curious and still no go.  I am starting to think it may be a hardware conflict.

---

### Post by Joebubba360 on 2009-11-02
I have the same identical issue. I thought it might be hardware related as well. However, I've tried using the Wubi installer on my Dell 630 with two partions (C: and D:) with the install on D:. I also tried the install on a friend's Lenovo Thinkpad T41 with the same setup. Both are running WinXp Sp3. Both were setup for a 30GB environment. Exactly the same results on both. This has to be a bug. I've tried reloading twice on both machines with the same results.

---

### Post by J-Becks on 2009-11-02
I had the same problem, but may have found the answer.  

During the installation process, Wubi was downloading the 64 bit 9.10 ISO, but given my computer, 32 bit is appropriate.  To force Wubi to dl the 32-bit version launch it from the command line:

wubi.exe --32 bit

that should run the installer and make it dl the 32 bit version.  I did this and everything worked the second time around.  This may have solved the issue, or just may have been a coincidence. 

Hope this helps.

---

### Post by blizbiggy on 2009-11-02
My pc is a x64 environment.  I do not think that is the problem, but the x86 version might work if forced.  I do not plan on trying it.

---

### Post by BeStanly on 2009-11-03
Hi all!
this is my first aport to this site. i hope to do it well.
The same problem happen to me. The problem is (aparently) is wubi Because this:
I had the same problem when i used the iso image wubi.
I downloaded the .iso image from the official site and wubi 9.10 ([wubi-installer.org/]("http://wubi-installer.org/")). Then I used (in my case) daemon tools for the image only for putting it in the virtual device but i didnt installed. then i used wubi and it reconized the image from the device. next wubi did the instalation normally AND THAT IS IT!!
if you do it you will notice that after you reboot, the installation will be in a elegant grafic user interface. thanks!!! i hope that this fix your problem up.

ps: My native language is spanish.excuse me if i did grammar mistakes;)

---

### Post by mikebaxter on 2009-11-03
I am getting the same screen - I have a new Dell Inspiron 1545 with 4GB RAM running WIN Vista

---

### Post by Joebubba360 on 2009-11-04
After spending a very frustrating weekend trying to get wubi 9.10 and Ubuntu 9.10 (32 bit) to load, I finally gave up when I realized the the grub loader which should be in the "Grub" folder, was missing. This was after redownloading the ISO image two different ways (from the site and via torrent). I've had to regress to 9.04. I hope someone comes up with a fix soon. 

The setup is loading the Ubuntu in Windows system on the D drive. This was tried on a Dell 630 and on a Lenovo Thinkpad T41. Same results in four attempts.

---

### Post by blizbiggy on 2009-11-04
I am just repartitioning my hard drive with the partitioner in ubuntu.  Worked fine on my laptop to do it that way... so too bad wubi was a failure for my desktop, so I will just repartition it too (since i have about 600gb of free space LOL)

---

