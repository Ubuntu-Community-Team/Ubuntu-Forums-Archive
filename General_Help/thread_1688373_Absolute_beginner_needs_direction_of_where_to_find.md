---
title: "Absolute beginner needs direction of where to find help."
date: 2011-02-15
forum: General Help
---

### Post by quantumpositron on 2011-02-15
Hi All,

I installed the latest version of Ubuntu as a hobby a few months ago.  Last night I followed instructions on how to get an MMO, Perfect World International, to run.  In a nutshell, I installed the ATI driver from the software updates and I installed Wine.  First version 1.0, then 1.2.  I successfully ran wine tricks after each wine install.  Everything the instructions said to do, I did, including installing directX from winetricks.  The game client was successfully downloaded and installed.  After running wine tricks I decided to reboot as recommended by the directX install.  And this is where things went wrong.  Ubuntu didn't boot.  It produced two very short lines of information so quickly I couldn't read it, and then rebooted my computer. I'm confident a knowledgeable user knows the solution to my dilemma, I am just not sure where to ask in the forums.  Is this a Wine issue?  A Ubuntu issue?  I am running 64 bit dual cores, is it a 64 bit issue?  Is it hardware related?  I am not sure where to go with my "situation."  All advice appreciated. 

-QP

---

### Post by dabl on 2011-02-15
When you try to boot your computer, what do you see?

---

### Post by sydbat on 2011-02-15
> **quantumpositron said:**
> Hi All,

I installed the latest version of Ubuntu as a hobby a few months ago.  Last night I followed instructions on how to get an MMO, Perfect World International, to run.  In a nutshell, I installed the ATI driver from the software updates and I installed Wine.  First version 1.0, then 1.2.  I successfully ran wine tricks after each wine install.  Everything the instructions said to do, I did, including installing directX from winetricks.  The game client was successfully downloaded and installed.  After running wine tricks I decided to reboot as recommended by the directX install.  And this is where things went wrong.  Ubuntu didn't boot.  It produced two very short lines of information so quickly I couldn't read it, and then rebooted my computer. I'm confident a knowledgeable user knows the solution to my dilemma, I am just not sure where to ask in the forums.  Is this a Wine issue?  A Ubuntu issue?  I am running 64 bit dual cores, is it a 64 bit issue?  Is it hardware related?  I am not sure where to go with my "situation."  All advice appreciated. 

-QPFirst, Welcome to the Ubuntu Forums.

Second, please use the "Enter" key to create paragraphs. One large block of text is very difficult to read properly.

Third, when WINE asks you to "reboot", it means to shut down WINE then open it up again. Linux is not Windows and does not require a reboot every time a bit of software is installed.

I doubt that it has anything to do with 64bit.

You say that your computer did reboot. Did Ubuntu boot at all? 

How do you have Ubuntu installed? Is it a dual boot situation? Did you install it via WUBI (as a "program" inside Windows)?

Not sure why you went through an "upgrade" type process to install wine. The current stable version is in the repositories (Software Centre or Synaptic).

EDIT - One more question...what is your graphics card? Is it ATI?

---

### Post by quantumpositron on 2011-02-15
Sorry for the long post.

I installed Ubuntu via the website.  Whatever program it runs set up my dual boot.  When I boot my comp goes through the BIOS screen, then a RAID detection screen (I have a mirror RAID), and then to a choose OS screen.

When I choose Ubuntu I get the following message:
"Try (hd0,0): NTFS5: No wubildr
 Try (hd0,1): NTFS5:_"

then the system does a complete reboot on its own.

Ubuntu does not boot at all.  I get the above message so fast I had to use a camcorder to catch it.

I chose Wine 1.0 because the description said it was stable.  I upgraded to 1.2 because someone on yahoo! answers said it was a better choice for PWI according to the wine wiki.  Clearly I am in better hands now. :)

My graphics card is an ATI RADEON 5770 by Powercolor.

After exhaustive detective work, installing drivers, playing with compatibility modes, etc. I cannot get higher than 20 FPS on minimal settings in Windows 7 64 bit. PWI tech support gave up.

Linux is a lot of fun, but I am just starting out.  Glad to hear it doesn't need reboots like windows.

Thank you for helping me with this.

---

### Post by bcbc on 2011-02-15
It sounds like you have Problem #2 as detailed here: [Wubi megathread]("http://ubuntuforums.org/showthread.php?t=1639198"). Solution #1 should fix it. There's a permanent fix after that.

---

### Post by requeth on 2011-02-16
A side bit of bad news from my experience. I only use ATI cards and I've found time and time again that wine doesn't support ATI for gaming. The best I've gotten is Starcraft 2 sitting on the opening screen flashing loading. Nvidia is very well supported, but ATI linux support isn't where it needs to be yet. They just started allowing OpenGL hooks last year.

---

### Post by quantumpositron on 2011-02-16
I'll try the solution in the Wubi post as you recommmended.  Thank you again!

Big goal for now is to get Ubuntu working normally and get the permanent fix bcbc mentioned.  In the PWI forums some people have gotten PWI to work with Ubuntu on ATI systems.  If I can't get it to work then I'll ebay my card and get an nVIDIA.  Likewise if I can't get the card to work at full capacity.

Does Wine seem to run your games better than Windows?

-QP

---

### Post by sydbat on 2011-02-16
> **quantumpositron said:**
> Does Wine seem to run your games better than Windows?Some games run way better in WINE than they ever did in Windows. Of course, this only applies to those that run in the first place.

---

### Post by quantumpositron on 2011-02-18
Hi guys.  Again, thank you for your time and patience.  I'm following the instructions that bcbc pointed me to and I've hit a snag:

I can't find grub.cfg for my ubuntu install.  I have used the search feature in the "file manager", so to speak, and have only been able to bring up what looks like sample grub.cfg and the grub.cfg for the live CD (judging by the file paths in their respective file properties.)

I have "Show Hidden Files" enabled.

My options in the "file manager" (sorry I don't know its real name):
"Ubuntu"
"Desktop"
"File System"
"Network"
"System Reserve"
"320 GB File System"
"Trash"
------------
"Documents"
"Music"
"Pictures"
"Videos"
"Downloads"

Searches in Ubuntu return 0 results, Desktop 0 of course, File System gives me the grub.cfg on the CD, and System Reserve and 320 GB File System give 0 returns.

Is this a really bad sign?

Thanks,
-QP

---

### Post by quantumpositron on 2011-02-18
Here is my results.txt from the script that is part of the instructions I am following.  I am uploading it because 

I have a raid mirror set up, and I am seeing some errors and stuff that is not like what's in the instructions.  

Would you guys take a quick browse?

---

### Post by bcbc on 2011-02-19
If you get errors along the way stop and report back. 
```
sudo mkdir /media/win
sudo mount /dev/mapper/nvidia_bfabbidi2 /media/win
sudo mount -o loop /media/win/ubuntu/disks/root.disk /mnt
sudo cp /mnt/boot/grub/grub.cfg /mnt/boot/grub/grub.cfg.bu
sudo chmod +w /mnt/boot/grub/grub.cfg
gksu /mnt/boot/grub/grub.cfg
```

Edit as described in wubi megathread. Save. Exit reboot into Wubi. Then apply the permanent fix as described in that thread.

---

### Post by quantumpositron on 2011-02-19
UPDATE:

I uninstalled the Wubi session of Ubuntu.  I took an extra HDD and did a clean install of Ubuntu onto it.

Everything is fine except I am not getting a dual boot menu.  So I am looking at how to set that up right now.

Please ignore my previous posts.  Thank you for helping me.  I hope its smooth sailing from here on out.

-QP

---

### Post by quantumpositron on 2011-02-19
Sorry bcbc, just saw your post.  Ubuntu is now on its own HDD, fully formated and partitioned via the LiveCD install.

Just gotta get this dual boot thing going and then I can move into Wine/ATI config.

It seems like I acted on poor information the first time with WINE.  I try to be a low maintenance noob.  

Can you give me some recommendations on where the official documentation is, so I don't blow it up again?

Thank you sir,

-QP

---

### Post by quantumpositron on 2011-02-19
Have a working boot manager: OSL2000.  When I select the Linux 

drive I get a blinking cursor, the screen goes black and seems to 

be trying to start, and...nothing.  It loops back to the cursor.

::sigh::

---

### Post by Morrad on 2011-02-19
> **quantumpositron said:**
> UPDATE:

I uninstalled the Wubi session of Ubuntu.  I took an extra HDD and did a clean install of Ubuntu onto it.

Everything is fine except I am not getting a dual boot menu.  So I am looking at how to set that up right now.

Please ignore my previous posts.  Thank you for helping me.  I hope its smooth sailing from here on out.

-QP

Correct me if I'm wrong, but it sounds like you now have something like:

[LIST]
[*] First hard disk (/dev/sda): Windows
[*] Second hard disk (/dev/sdb): Linux
[/LIST]

... and when you restart your computer, it jumps into Windows rather than showing the grub menu.

The grub boot loader needs to be installed onto the first hard drive (/dev/sda).  To do this, you can either:

[LIST=1]
[*] Reinstall Ubuntu onto your second hard drive, and when then select the first hard disk (/dev/sda) when it asks you where to install grub.  This may be the most straightforward approach.
[*] Use the Ubuntu livecd to reinstall grub.  To do this, boot off the livecd, get a terminal, and use this guide ([http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)) to reinstall grub.  Note that you will need to know exactly which drive partition your boot folder is in (it will be hd1,something.  /dev/sdb1 is (hd1,0), /dev/sdb2 is (hd1,1), and so on.).  If you're not sure, it would probably be easiest and safest for you to reinstall like I said above.
[/LIST]

---

### Post by quantumpositron on 2011-02-19
It seems to depend on what program you ask, and possibly my level of technical knowledge, which is not much:

Disk utility sees two 320 GB ATA drives. It calls one sda1, and the other sda2.

GParted sees two partitions.  One is 100MB, called sda1.  The other is 297GB and called sda2.


I have two 320 GB ATA hard drives that are configured in a RAID mirror.

---

### Post by quantumpositron on 2011-02-19
Worked with the gnome partition app and checked my partitions before possibly resizing.

It said something along the lines of "this is not a good idea for you."

So I rebooted.  And now Windows won't boot.  It loops the Win 7 loading animation and the windows recovery app says its unfixable.  

I unplugged my SATA drives, disabled RAID in the BIOS, and plugged in the 40GB IDE drive that I installed Ubuntu on.  

It wouldn't boot with the SATA drives plugged in but will boot now.  So, at least I have a working OS with internet connectivity.

---

### Post by quantumpositron on 2011-02-23
The WINE wiki has a support page for playing Perfect World International.  I followed it to the T:

1.  Install WINE 1.2
2.  configure WINE as outlined.
3.  Edit the registry as outlined.
4.  Install PWI.

It works.  I am using the flgxr driver and can run the game at max resolution with maximum settings.  

The frames per second is the same as it was in windows 7 64bit:  10.  

The HD 5770 hardware can handle PWI graphics.  So can my AMD II X2 and 4GB RAM.

This makes me think there is something going on between the game and the ATI driver.  

The only difference between Win7 and Ubunutu with this game is that it locks up in Ubuntu, which I have read is not uncommon with ATI cards.

---

