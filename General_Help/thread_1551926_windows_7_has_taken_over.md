---
title: "windows 7 has taken over"
date: 2010-08-12
forum: General Help
---

### Post by texasboy2084 on 2010-08-12
I love Ubuntu, I wiped windows and gave everything to Ubuntu. But I miss World of Warcraft and failed many times to get it to work on Ubuntu. So I made a 50 gig partition just for Windows 7 to run WoW. Now windows won't let me boot into Ubuntu on start.
I have checked and this partition is the 50 gigs I wanted it to be. But how to I get back to Ubuntu? Any help will be appericated.
 
 
Thanks in advance :D

---

### Post by ST3ALTHPSYCH0 on 2010-08-12
Reinstall GRUB:
[http://www.google.com/search?q=reinstall+grub&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a](http://www.google.com/search?q=reinstall+grub&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a)

---

### Post by stinkeye on 2010-08-13
> **ST3ALTHPSYCH0 said:**
> Reinstall GRUB:
[http://www.google.com/search?q=reinstall+grub&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a](http://www.google.com/search?q=reinstall+grub&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a)

Why give a link to a google search for reinstall grub to an obviously fairly new user? I'm sure they know how to use google.
The first part of this post should explain how to reinstall grub.
[**_[COLOR="DarkRed"]http://ubuntuforums.org/showthread.php?t=1014708[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=1014708")

---

### Post by texasboy2084 on 2010-08-13
Thanks that search had the showed the same topic. I followed the steps listed, now grub shows but thats just it... it only shows "grub" on boot up:


grub>

The only way I can use and OS to post this is buy using my livecd.  Also i didnt mind the google search now I know the name of the boot loader.  But upon googling "grub only showing grub" none of the results seemed to work. On the livecd it looks like my partitions are still there.

---

### Post by worksofcraft on 2010-08-13
Never install Windows with a Linux distro present. Microsoft quake in fear at the word "Linux" and so every single update you get from can potentially wipe your Ubuntu :(

What you must do is get a separate hard drive for Microsoft installations. It can be a really cheap and crappy old IDE drive. They are ideal for windblows. Then disconnect the Sata cable from your proper Ubuntu and install the Microsucks products. All you have to do is reconnect the Ubuntu drive and run update-grub. That will identify the Windoze installation and add it to your boot menu :)

---

### Post by texasboy2084 on 2010-08-13
To correct this problem can I:

Run my gparted Livecd and extend my Ubuntu partition deleting Windows. Then use the Ubuntu Livecd to uninstall grub?

---

### Post by worksofcraft on 2010-08-13
> **texasboy2084 said:**
> To correct this problem can I:

Run my gparted Livecd and extend my Ubuntu partition deleting Windows. Then use the Ubuntu Livecd to uninstall grub?

No. Linux distros all have to be booted by GRand Unified Bootloader. I suggest you simply try to reinstall Grub.. well actually go for Grub2 that comes with Lucid Lynx CD.

I never had these problems because I always disconnect my Ubuntu drives when I install, or upgrade Micros*ft products. Thus not quite sure, but I suspect all you have to do is boot to a Ubuntu command prompt somehow and then run

sudo update-grub

you will need some kind of superuser password... I just wish it asked the Windblows installation disk for one before it overwrites your MBR :shock:

---

### Post by luffy_chan_19 on 2010-08-13
hmmm my suggestion is that you could unplug the power from the ubuntu drive every time u want to run windows 7 and install windows 7 on that disk, and then when you want to use ubunt u plug the drive back in. thats my best suggestion.... oh wait u have it on the same disk... wow.... reinstall grub. from terminal

---

### Post by stinkeye on 2010-08-13
> **texasboy2084 said:**
> Thanks that search had the showed the same topic. I followed the steps listed, now grub shows but thats just it... it only shows "grub" on boot up:


grub>

The only way I can use and OS to post this is buy using my livecd.  Also i didnt mind the google search now I know the name of the boot loader.  But upon googling "grub only showing grub" none of the results seemed to work. On the livecd it looks like my partitions are still there.

Check that that the partition you installed Ubuntu on (sudo fdisk -l) is what you used for all the sda5 enties in the link I gave you.


eg.
```
sudo mkdir /media/[COLOR="Magenta"]sda5[/COLOR]
sudo mount /dev/[COLOR="#ff00ff"]sda5[/COLOR] /media/[COLOR="#ff00ff"]sda5[/COLOR]
```
```
sudo grub-install --root-directory=/media/[COLOR="#ff00ff"]sda5[/COLOR] /dev/sda
```
[COLOR="#ff00ff"]Your Ubuntu partitition.[/COLOR]

---

### Post by Grenage on 2010-08-13
> **worksofcraft said:**
> Never install Windows with a Linux distro present. Microsoft quake in fear at the word "Linux" and so every single update you get from them will wipe your Ubuntu :(

What you must do is get a separate hard drive for Microsoft installations. It can be a really cheap and crappy old IDE drive. They are ideal for windblows. Then disconnect the Sata cable from your proper Ubuntu and install the Microsucks products. All you have to do is reconnect the Ubuntu drive and run update-grub. That will identify the Windoze installation and add it to your boot menu :)

I'm sorry, but that is completely incorrect and misleading information.

---

### Post by worksofcraft on 2010-08-13
> **Grenage said:**
> I'm sorry, but that is completely incorrect and misleading information.

Whenever I have install Windows it has trashed pre-existing Ubuntu installations and/or my boot setup. IMHO you need to either install Windows first and then add Ubuntu or disconnect your working Linux drives when installing Windows.

However if you can explain another way to install windows safely without risking your Linux setup then do feel free to give more accurate instructions!

---

### Post by Grenage on 2010-08-13
> **worksofcraft said:**
> Whenever I have install Windows it has trashed pre-existing Ubuntu installations and/or my boot setup. IMHO you need to either install Windows first and then add Ubuntu or disconnect your working Linux drives when installing Windows.

However if you can explain another way to install windows safely without risking your Linux setup then do feel free to give more accurate instructions!

My main gripe was your statement that every single update from MS will wipe Ubuntu.  That's not just a bit wrong, it's a complete lie.

You can install Windows after Linux, you just need to use a LiveCD to reinstall grub.

---

### Post by worksofcraft on 2010-08-13
> **Grenage said:**
> My main gripe was your statement that every single update from MS will wipe Ubuntu.  That's not just a bit wrong, it's a complete lie.

You can install Windows after Linux, you just need to use a LiveCD to reinstall grub.

OK I've edited it now so it only says it CAN trash your Linux. However I don't consider it was a "complete lie" because having to use a live Ubuntu installation disk after doing your Windows upgrade counts as a trashed installation in my book: Imagine if you had to use a live Windows CD to restore Windows after upgrading Ubuntu! Also I had worse problems than a corrupted boot partition, so it's not worth the risk TBH, just unplug the cable.

---

### Post by Grenage on 2010-08-13
Aye, but I've not actually seen a Windows update change the bootloader.  I'm not sure it's ever been patched?

---

### Post by ST3ALTHPSYCH0 on 2010-08-13
Yeah, been running a Win7 Ubuntu dual boot for a year now.... the only updates that have trashed my Ubuntu install have been *gasp* Ubuntu updates. While there are lots of people who install their OSes with only one disk installed and then use the boot selector in BIOS, it's not the only, or even most proper, way to dual boot (Win98 installs on the second disk aside).

---

### Post by Mark Phelps on 2010-08-13
> **Grenage said:**
> Aye, but I've not actually seen a Windows update change the bootloader.

+1

I've been running multi-boot systems with various versions of MS Windows since Ubuntu 7.04 -- and never ONCE, has a Windows Update messed with GRUB (or more recently, GRUB2) in any way.

---

### Post by texasboy2084 on 2010-08-13
Well I  checked again and I still cant boot right.  If you type "sudo grub" in to your terminal you will see:

(alot of words here)

grub>

That is what I see on start up.  Also I'm not sure if this makes a difference but I am on a laptop.

---

### Post by sheepo on 2010-08-13
Odd. But yes, when you install an OS such as Windows, it overrights GRUB.

---

### Post by texasboy2084 on 2010-08-13
Well, I'm about ready to do a clean install. I don't have nothing major on my hard drive that I can't reinstall again.  But before I do could I install Ubuntu again on a separate partition (then I would have 3), then delete the old Ubuntu and keep my old files? Then hope to have everything working right?


Again thanks for the help :)

---

### Post by linux18 on 2010-08-13
> **texasboy2084 said:**
> Well I  checked again and I still cant boot right.  If you type "sudo grub" in to your terminal you will see:

(alot of words here)

grub>

That is what I see on start up.  Also I'm not sure if this makes a difference but I am on a laptop.
sudo update-grub

---

### Post by texasboy2084 on 2010-08-13
That helped I am now able to get Ubuntu to boot, now Windows won't lol. I'll check out that other post, for the windows problem. Thanks alot :)

---

### Post by Grenage on 2010-08-13
Sometimes when you update Grub, it doesn't detect the Windows 7 install.  I *think* (while since I had this) it was down to a folder with a certain name in Window's root drive.  I think it might have been 'data' or something.  Possibly one called **D**ata and one called **d**ata.  I had to delete the incorrect one.

Don't delete anything unless sure, and take a backup.

---

### Post by DrMelon on 2010-08-13
> **worksofcraft said:**
> Never install Windows with a Linux distro present. Microsoft quake in fear at the word "Linux" and so every single update you get from can potentially wipe your Ubuntu :(

What you must do is get a separate hard drive for Microsoft installations. It can be a really cheap and crappy old IDE drive. They are ideal for windblows. Then disconnect the Sata cable from your proper Ubuntu and install the Microsucks products. All you have to do is reconnect the Ubuntu drive and run update-grub. That will identify the Windoze installation and add it to your boot menu :)

Dismiss this advice. I've dual booted Windows 7 for close on 6 months now, getting updates along the way. It works just fine.

---

