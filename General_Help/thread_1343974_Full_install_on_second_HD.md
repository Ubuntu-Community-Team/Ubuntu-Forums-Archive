---
title: "Full install on second HD"
date: 2009-12-02
forum: General Help
---

### Post by johnhdsi on 2009-12-02
Hi all, quick question ( I hope easy answer) on doing a full install of 9.10 on a second HD.

I have Win Xp loaded on my main HD and I have another drive which I had laying around and I want to load 9.10 on it. So there's less confusion I'll call my main drive with XP on it sda and the second drive I want to install 9.10 on sdb. 

When I go to install 9.10 on sdb I see an advanced option that has boot options. What I want is to be able to select either XP or 9.10 from the boot menu (such as the case when I did my Wubi install inside windows). What I dont understand is where I need to have the loader installed. Do I install the loader to sdb or sda? I'm trying to be very careful here as I can't afford to mess up my Win install cause it's my work pc. So the short version of my question is how do I make my 9.10 install on a separate drive show up like the Wubi installer does?

Hope that made sense, bear with me please I'm learning all of this as I go. Any info would be much appreciated!!!.

John

---

### Post by ankspo71 on 2009-12-02
Hi John,

If you want to install grub on the ubuntu drive (the second drive) then you will have to swap the boot priority so that the ubuntu drive (the second drive) will boot first... so grub will work on the Ubuntu drive. This way everything that is related to ubuntu will be on one drive and will not interfere with the windows bootloader if you ever decide to remove ubuntu.

So before installing Ubuntu, change the boot priority so that windows will boot second. Just remember that you changed the boot priority later on. If you decide to remove linux (or reinstall windows), change the boot order back to the way it was.

Also, if you can swap drives by using a hotkey during startup, you can simply choose which drive to boot from. (my computer doesn't support this feature, but maybe your's does)

If for some reason in the future you need to repair the windows bootloader, supergrubdisk makes it easier to do.

Edit: This advice is typically for those that can't afford to overwrite the window's MBR (bootloader) and dual booting separate  hard drives.

hope this helps explain a little,
James

---

### Post by johnhdsi on 2009-12-02
Lol..I hate being a noob...


Question 1. How would I change the boot order of windows/Ubuntu? Would this be done in the bios by switching my boot priority on drives?

Question 2. Grub is......(Sorry NOOB!!!) the O/S loader for Ubuntu correct? This determines what kernel and settings you are booting with?

I don't have or know of a hot key for switching drives at startup so I am assuming I don't have anything like that. Every time I have installed ubuntu on a machine I have either full installed on a drive with no Windows O/S or done the Wubi install inside Win and gone from there.

Don't mean to be a pain in the butt with the second post of questions, I just want to get it right the first time around and not do the "OH CRAP!" dance lol

---

### Post by ankspo71 on 2009-12-02
Hi, 

1) yes the boot priority I am referring to is found in the bios.  
You would want to change the boot priorities to something this:
1 cdrom would be first
2 ubuntu hard drive 
3 windows hard drive

(if you have a floppy drive you probably want to put that first, followed by the cdrom and so on.)

2) Yes, Grub is the bootloader for Ubuntu.

Once you get the boot priority sorted out, you can install ubuntu to the unused hard drive. Being that you are dual booting separate drives, I highly recommend using manual partitioning when you get to Ubuntu's partition manager (unless the automatic partitioner shows that you can install to the empty hard drive).

Ubuntu's partitioning should be something like this...

/          (root partition)   ext3 or 4
/home                          ext3 or 4
/swap   

/Swap doesn't need to be bigger than 2gb, unless the user puts the computer through extremes. 

The size of /root depends on how much software you will be installing. 8-10gb is enough /root for the average user (but I recommend larger for gamers). 

a separate partition for home is not required, but it is good for things like upgrading to a newer ubuntu later on. 

hope this helps.
James

---

### Post by johnhdsi on 2009-12-02
Yes it did, thank you so much for the info. I got it installed and the grub loader gives me the option of Ubuntu or Win exactly the way I wanted it to be. This is why I love these forums, you guys know your stuff and can explain it so people can understand what you are saying. Thanks so very much!!!!

John :D

---

