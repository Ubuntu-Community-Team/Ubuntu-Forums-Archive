---
title: "Ubuntu 10.04 freezes / locks up when using hard drive"
date: 2010-05-05
forum: General Help
---

### Post by My_web on 2010-05-05
Hi all,

I've just installed 10.04 as a dual boot with Windows 7. I did a clean install removing my old 9.10 install.

I really like all the changes I've seen so far and everything seems to work smoothly except when the HD is being used a lot everything freezes and then un-freezes again and again until the file operation has stopped.

The problem really only comes up with heavy operations like moving large files (I moved a 10gb vdi from my Windows partition to Ubuntu) and when backintime does it's daily backup. Sometimes I can continue using it then it'll freeze I wait.. can use it again for a bit then it will freeze again.

Any ideas on this? I've never had problems with transferring large files on the Windows 7 install so I don't think there's a hardware problem. I can't seem to find anything I've been searching for two days now. I did find something about a problem with backintime/ext4 partitions but the solution hasn't helped.

I would really appreciate any help as I prefer working on Ubuntu but it's a bit difficult at the moment.. :icon_frown:

---

### Post by Vandres on 2010-05-05
Same thing here, i use windows 7 and install 10.04 after used 9.10 same issues ubuntu freezes when move large files or download packages from the net.
 
I hope somebody could answer 

Regards

---

### Post by sparkythewondersquid on 2010-05-06
Same here it is very annoying (I dont care for grub2 also)

---

### Post by Sallah Adim on 2010-05-06
Hi everybody,

I too am new to Ubuntu. 
I did a fresh install of Lucid Lynx on an old Sony Vaio laptop after replacing its hard drive.
It went fine and instaled properly.
However, when updating the system, it tends to freeze, forcing me to a hard reboot, while installing new packages. Generaly it does that after working properly for five minutes.
I suspected a hardware problem so i replaced the hard drive. That improved matters and now the system only freezes after about fifteen minutes. But it still freezes though!
The laptop has a P4 processor (1.6Ghz) and 512 Mb of RAM so it is normaly within the minimum required to install Ubuntu 10.04.
I would really like to fix this in order to use this new OS fully. 
Does anybody have any idea or tips to do so?

Thanks a lot in advance.
Rgds,

Sallah Adim from Altaïr

---

### Post by rauldinho on 2010-05-06
Same case here. When i'm using ubuntu it freezes when updating the system.

---

### Post by ububaba on 2010-05-06
Please go through this link. It is helpful.

[http://ubuntuforums.org/showthread.php?t=1473131&highlight=lucid+freeze](http://ubuntuforums.org/showthread.php?t=1473131&highlight=lucid+freeze)

---

### Post by raja_ram on 2010-05-08
i dont know whether it is related to hard drive.
my ubuntu just freezes, not even a mouse move. i am having to restart it. this is when we go into the GNOME mode. this does not happen in the failsafe mode... 
im aware working in failsafe mode is not advisable.

please help 

thanks
raja

---

### Post by guicord on 2010-05-08
Hi, my Ubuntu 10.04 also freezes, but during periods of inactivity, I'm not sure after how long, sometimes 2h, sometimes not. The screen is dark, it doesn't react to ctrl+alt+del or the Num key... only a hard reboot does it. The same machine worked well with 9.10. I don't know yet were to look at to troubleshoot, any hint would be appreciated. 
Thanks, Guillaume
==
AMD Athlon 64 3200+ 2.20Ghz
1GB of DDR400 RAM Supertalent 
Zotac Nvidia GeForce 8500GT 512MB video card

---

### Post by bigjeff1002 on 2010-05-08
> **My_web said:**
> Hi all,

I've just installed 10.04 as a dual boot with Windows 7. I did a clean install removing my old 9.10 install.

I really like all the changes I've seen so far and everything seems to work smoothly except when the HD is being used a lot everything freezes and then un-freezes again and again until the file operation has stopped.

The problem really only comes up with heavy operations like moving large files (I moved a 10gb vdi from my Windows partition to Ubuntu) and when backintime does it's daily backup. Sometimes I can continue using it then it'll freeze I wait.. can use it again for a bit then it will freeze again.

Any ideas on this? I've never had problems with transferring large files on the Windows 7 install so I don't think there's a hardware problem. I can't seem to find anything I've been searching for two days now. I did find something about a problem with backintime/ext4 partitions but the solution hasn't helped.

I would really appreciate any help as I prefer working on Ubuntu but it's a bit difficult at the moment.. :icon_frown:

HELP! Ubuntu 10.04 (Lucid) Freezing and hanging for several seconds when I click on a page, file, etc., both on-line and off-line.
Running Nvidia graphics card on a Dell M6400 Precision Workstation.  This is driving me crazy!  What to do?  Would be deeply grateful for help.  [email]bigjeff1002@yahoo.com[/email].

---

### Post by bigjeff1002 on 2010-05-08
[center]ubuntu freezing & hanging

[/center]> **bigjeff1002 said:**
> help!** ubuntu 10.04 (lucid) freezing and hanging** for several seconds when i click on a page, file, etc., both on-line and off-line.
Running nvidia graphics card on a dell m6400 precision workstation.  This is driving me crazy!  What to do?  Would be deeply grateful for any help and welcome responses directly to my email. . :confused:  [email]bigjeff1002@yahoo.com[/email].

---

### Post by lnthai2002 on 2010-05-12
I have the same problem. I upgrade from 9.10, everything went fine. But after a while between 2-8h (i was downloading something) it locked up. Nothing on the screen, the system doesnt seem to react to any keyboard or mouse input. I have to manually reset to bring it back. Yesterday, it happened again after 1h while waiting to shutdown (sudo shutdown -hP +120) and then even the reset button doesnt bring it back, I have to unplug the power cable and plug it back to restart the machine. I doubt if it's hardware issue since my windows 7 is running just fine. 
Any suggestion would be appreciated. BTW, i i'm running 32x kernel with pae.
Thanks in advance

---

### Post by thogomedia on 2010-05-14
I dualboot  ubuntu 10.04 with Vista

first everything worked alright but after I installed ntfs-config to automount my ntfs partitions and rebooted, everytime I accessed my partition or another place on the hard drive the systems freezes.
But I can still use my mouse.

Also it unfreezes, and freezes again

Hope we can find a solution very fast, because I do all my work on ubuntu and I hate working with vista!


Greetz,

---

### Post by bigjeff1002 on 2010-05-14
**Linux Freezing**

HELP! Ubuntu 10.04 (Lucid) Freezing and hanging for several seconds when I click on a page, file, etc., both on-line and off-line. Running Nvidia graphics card on a Dell M6400, Precision Workstation.  This is driving me crazy!  What to do?  Would be deeply grateful for help. Alot of people seem to be having this problem, but I have not seen any posts with a solution. HELP! Must we wait for a stable release of 10.04? [email]bigjeff1002@yahoo.com[/email]

---

### Post by szabouk on 2010-05-16
> **bigjeff1002 said:**
> **Linux Freezing**

HELP! Ubuntu 10.04 (Lucid) Freezing and hanging for several seconds when I click on a page, file, etc., both on-line and off-line. Running Nvidia graphics card on a Dell M6400, Precision Workstation.  This is driving me crazy!  What to do?  Would be deeply grateful for help. Alot of people seem to be having this problem, but I have not seen any posts with a solution. HELP! Must we wait for a stable release of 10.04? [email]bigjeff1002@yahoo.com[/email]

hi;

you can try to disable compiz and/or the best would be to install 10.04 again and try to format your HDD using ext3 fs.

please try not using nvidia driver and let me know if you still have errors...

hope it helps

__z

---

### Post by jybumaat on 2010-05-26
In my case both using the live CD and installing Ubuntu 10.04 on my Intel based chipset motherboard freezes after logging in for several minutes.  When I disabled compiz the freezing problems stops.  I guess there is a problem between compiz and X server...:confused:

---

### Post by lifetonjoyu on 2010-05-27
my problem is also same as wat raja is facing.......in failsafe mode it is working fine but it didnt show the network manager icon in it.....while it freezes in GNOME mode............ somebody with solution plz come up

---

### Post by jolig on 2010-06-16
Same here.

I've updated from 9.10 to 10.04 and I get freeze too when writing large files on my hdd.
I'm using a Gigabyte motherboard with a P43 Intel Chipset.
My GFX is ATI 4650 in PCIe Gen2.
My HDD is a 500GB Samsung F2 running on the Native AHCI Intel Controller.

---

### Post by jolig on 2010-06-17
Does anyone else facing the same issue can post its configuration to try to cross our HW ?

---

### Post by jolig on 2010-06-18
Up

---

### Post by jolig on 2010-06-19
The simple fact to extract a big archive (rar/zip) from my local HDD to my local HDD make my computer freezing while the unrar is processing (it take about 25% of my CPU ressources) and I last in about 1 minute for a couple of GB archive which seems to be fine.

I do not have anything strange in dmesg.

Any help to find what's going on ?

---

### Post by jolig on 2010-06-28
It is definitly related to 10.04 as i've run a 9.10 livecd and the issue is not present :(

Any hint ? :(

---

### Post by GarthS on 2010-06-29
I suggest you guys check out the following thread...
 
**Ubuntu 10.04 (Lucid Lynx) Random Freeze / Hang-up**

It's the biggest thread going on this 10.04 freezing issue. There is a lot of comprehensive information in that thread about this issue. 

SPOILER ALERT: The issue is still not resolved.  :frown:
It seems there a multiple issues causing the freezing. A fix that works for one hardware configuration won't work for another....But there may be a fix in that thread that works for your hardware config. Unfortunately none worked for me, so I've gone back to 9.10 until the powers that be get this whole mess straightened out once and for all. 

Good luck everyone! :)

---

### Post by sgvaibhav on 2010-06-29
oh no..
i downloaded latest ubuntu yesterday... (downloaded iso file, did not install it though).
i'm planning for a COMPLETE Hard-disk format and then i was going to dual boot windows xp along with ubuntu 10.04...

hmm i will only install xp now.... i prefer to wait till this gets fixed, so i can install it then...

---

### Post by deVega on 2010-07-03
Hi all,

Large File Operations Freezes very frustrate... everything else works fine. i can continue working even the file Operations freezes  but can't copy files. this is a big issue for an OS.

 i have install Ubuntu  on a new PC ( just 3 days working with it) all HD's are new with ext4 File system.


Thanks for any advice.

---

### Post by deVega on 2010-07-07
my problem with file operations in ubuntu 10.04: 
[http://ubuntuforums.org/showthread.php?t=1473475](http://ubuntuforums.org/showthread.php?t=1473475)

i have solve this problem and is not an ubuntu issue.
bad network configurations and bad hardware bring also bad results.
in my case i have change the router and the SATA/IDE controller also replace the Network card and cables cat with cat6 cables. All this replacements offers me 1G Lan and MTU at 9000 for JUMBO FRAMES.

After this hardware changes the file operation works perfect for me. i can now transfer large files locally and over the network 
(12-15 MB/s) without any freezing problem. 

i will continue testing with Ubuntu 10.04. i like it very much!:D

---

### Post by sallymc on 2010-07-12
> **GarthS said:**
> I suggest you guys check out the following thread...
 
**Ubuntu 10.04 (Lucid Lynx) Random Freeze / Hang-up**

It's the biggest thread going on this 10.04 freezing issue. There is a lot of comprehensive information in that thread about this issue. 

SPOILER ALERT: The issue is still not resolved.  :frown:
It seems there a multiple issues causing the freezing. A fix that works for one hardware configuration won't work for another....But there may be a fix in that thread that works for your hardware config. Unfortunately none worked for me, so I've gone back to 9.10 until the powers that be get this whole mess straightened out once and for all. 

Good luck everyone! :)

Same story with me.  Am so frustrated - have had 3 new hard drives installed!

Have decided to regress to 9.10, but need some advice please.   Do I just clean my HD and reinstall 9.10?  Terrified it will freeze in the middle of the process.

Thanks in advance.

---

### Post by jolig on 2010-08-03
Any Update ?

It seems to be related to ext4 on my side.
I used an ext3 hdd recently and I didn't noticed any freezing while copying large files...

---

### Post by tedjordan on 2013-03-26
I realize this is 3 years too late, but I just upgraded to 10.04.  I prefer to stay 1 major
version behind hoping to have fewer problems, but after the upgrade from 8.04 my
system started locking up.

the workaround for me was to switch off of gnome desktop and convert to the
kde or xfce desktop. 

That worked for me

---

### Post by Elfy on 2013-03-26
Old threaad closed.

---

