---
title: "Upgrading XP Home to Pro with Ubuntu"
date: 2010-04-20
forum: General Help
---

### Post by cajunflavoredbob on 2010-04-20
I have been using Karmic Ubuntu for a while now with XP Home. I need to upgrade to XP Pro. Am I going to need to reinstall everything on both partitions or will this affect only the Windows partition?

---

### Post by 2048Megabytes on 2010-04-20
[SIZE="2"]My guess is likely you are going to reinstall everything on your hard drive.  Backup all your important data to a separate storage device _before_ you try to upgrade.

I would also recommend you upgrade to Ubuntu 9.04 Jaunty Jackalope.  It is better than Karmic Koala.[/SIZE]

---

### Post by Sin@Sin-Sacrifice on 2010-04-20
No... no no. Unless you installed ubuntu using wubi nothing on Ubuntu will be affected and Jaunty is older and only sometimes better. I found Karmic to be much better and now find Lucid to be even more so but it's up to you to test out which version works best for you.

---

### Post by Roasted on 2010-04-20
> **Sin@Sin-Sacrifice said:**
> No... no no. Unless you installed ubuntu using wubi nothing on Ubuntu will be affected and Jaunty is older and only sometimes better. I found Karmic to be much better and now find Lucid to be even more so but it's up to you to test out which version works best for you.

This. ^ 

Jaunty was pretty solid, but Karmic has aged and as such, I wouldn't consider it lacking compared to Jaunty at all.

However, this close to Lucid, perhaps you should consider waiting a few more days for that.

---

### Post by cajunflavoredbob on 2010-04-20
Thanks for the help, guys. I'm new to the Linux universe. I tried out Jaunty before I used Karmic. I prefer Karmic so far, but I'm looking forward to Lucid.

---

### Post by Native Dialect on 2010-04-20
Back up your Ubuntu partition, just in case. I lost a ton of school work at the end of my last academic quarter, because I upgraded from Windows Vista to Windows 7. It replaced GRUB with the Windows MBR. I didn't think that would be an issue, so I tried to reinstall GRUB, but the end result was that my work was lost. 

Hypothetically speaking though, an upgrade should only affect the partition you are upgrading, not the entire drive. Hypothetically. And Karmic is very stable now. When it first launched, it was problematic. but these days, it is nearly flawless. It has far better integration of the sound API (no more selecting ALSA, OSS, Pulse etc. You simply choose your audio device and how it outputs). It has really solid driver support across the board actually. I would be excited for Lynx, but the GUI change is a bit of a turn off. I will have to wait and see what they do with it, other than make it look like Mac OSX.

---

### Post by 2048Megabytes on 2010-04-20
> **Sin@Sin-Sacrifice said:**
> No... no no. Unless you installed Ubuntu using wubi nothing on Ubuntu will be affected and Jaunty is older and only sometimes better. I found Karmic to be much better and now find Lucid to be even more so but it's up to you to test out which version works best for you.

Good to hear they have worked the bugs out of Ubuntu 9.10.  Last time I was thinking of installing version 9.10 around January 2010 it had many problems.  I just reinstalled Windows and Ubuntu 9.04 on my hard drive and everything is running fine except my VLC Media Player.  

Also the AMD Phenom II Quad-Core Processor is a beast and runs Flight Simulator X well.

---

### Post by uRock on 2010-04-20
Jaunty and Karmic are both rock solid. I would never recommend someone go to an older release unless the one they are using is incompatible. You will most likely have to reinstall Ubuntu. Whenever doing Windows installs backups are a must.

Cheers,
Ronnie

---

### Post by earthman on 2010-04-20
Windows will overwrite your GRUB installation, as you may be aware. You may need to at least reinstall that.

---

### Post by oldtraveler on 2010-04-20
Since Windows tends to overwrite GRUB 2 at times, I keep a separate small partition available for Ubuntu 9.04 which uses Grub Legacy.  Grub Legacy does not easily get overwritten by Windows so if Ubuntu 9.04 is the last OS installed then it recognizes all other existing OS.   Thus should a new Windows OS create an MBR all I need to do is to re-install Ubuntu 9.04 with a new Grub Legacy.

---

### Post by garvinrick4 on 2010-04-20
It will over write the grub 2  here is a link to reinstall grub2. Just a couple of lines of code.

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)


If you are going to install Ubuntu after xp pro then do not worry about it. Ubuntu will put
grub2 back in its place.

---

### Post by cajunflavoredbob on 2010-04-21
I tried installing XP Pro, but as it turns out, if it can't read PART of the HDD, even if it is in another partition, it refuses to read the HDD at all and tells you that there is no HDD installed. I'm going to have to manually remove Ubuntu and try again. DAMN YOU, MICROSOFT! Why can't we all just get along?!

---

### Post by cajunflavoredbob on 2010-04-21
How do I go about creating a proper backup of my settings in Ubuntu to an external HDD?

---

### Post by oldtraveler on 2010-04-21
You could create an image of your Ubuntu OS using PING [http://ping.windowsdream.com/](http://ping.windowsdream.com/)
From that you could restore Ubuntu at any time.

---

### Post by Mark Phelps on 2010-04-21
PING most likely will NOT work because it uses partimage -- which can not handle Ext4 filesystems.  So, if you defaulted to Ext4 for your Karmic install, you can't use PING.

You would do better using Clonezilla.

---

### Post by oldtraveler on 2010-04-21
> **Mark Phelps said:**
> PING most likely will NOT work because it uses partimage -- which can not handle Ext4 filesystems.  So, if you defaulted to Ext4 for your Karmic install, you can't use PING.

You would do better using Clonezilla.
I just discovered PING when I tried to make an image of Ubuntu 10.04 using Clonezilla and it wouldn't work after trying twice.  So I used PING and it did work.  I even tested the image from PING by doing a restore.

---

### Post by cajunflavoredbob on 2010-04-21
Neither one seems to be working for me. I'm just going to back up my important stuff and redo both of them.

---

### Post by egalvan on 2010-04-21
> **cajunflavoredbob said:**
> Neither one seems to be working for me. I'm just going t**o back up my important stuff and redo both of them.**

Since you are going to BACK UP YOUR IMPORTANT STUFF ANYWAY...

why don't you try this experiment...

if it fails, you've just lost a little time.
if it works, you saved your Linux install...

Download SuperGrub, burn to CD, and boot it.

Save the **bootloader** code portion of the MBR to a thumb drive.
DO NOT save the entire MBR... you don't want the partiton table info, just the bootloader.
it's about 412 bytes long

Re-install a Windows MBR (it's also called "fixing a Windows MBR")

re-boot using your XP-Pro CD...

it SHOULD now see the drive... and the original XP-Home install...

do the XP-Pro thing,

when done, and XP-pro is booting OK, 
re-boot SuperGrub, and have it reload the saved bootloader code.

This should get you back to your original GRUB boot.

and your original Ubuntu installation.


if not, go with your original plan :)

---

### Post by waynefoutz on 2010-04-21
> **cajunflavoredbob said:**
> I tried installing XP Pro, but as it turns out, if it can't read PART of the HDD, even if it is in another partition, it refuses to read the HDD at all and tells you that there is no HDD installed. I'm going to have to manually remove Ubuntu and try again. DAMN YOU, MICROSOFT! Why can't we all just get along?!

You're installing a ten year old OS. It has no idea what a ext4 file system is.

---

