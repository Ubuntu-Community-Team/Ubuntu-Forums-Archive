---
title: "Install Grub on MBR with Ubuntu Live CD to run Windows partition"
date: 2006-06-17
forum: General Help
---

### Post by rookee on 2006-06-17
Hi!

I deleted my old Gentoo partitions (boot, root, swap) to prepare for a new Ubuntu installation. I used Grub as boot manager to multi boot Win XP and the Gentoo installation. Now after deleting every trace of the old Linux installation, Grub wont start and I cant  get to my Windows partition.

How can re-install or re-configure Grub (to the MBR) to make everything work again? I have two partitions on the disk at the moment; they're both fat32 windows partitions where the first one has the operative system and the second is for file archiving.

I tried installing Grub through the Live CD (apt-get install grub) and when I ran it, I typed [FONT="Courier New"]root (hd0,0)[/FONT] (since my primary windows partition is hda1). Then what? Is it even possible to get Grub running from the MBR using only the Live CD? I tried using the install CD (not an option) and I've done some searching, but all help is directed for the ones trying to set up Grub for a multi-Linux-Windows-boot where there is a boot partition involved.

Basically, I want Grub to boot Windows for me and I want to use the Ubuntu Live CD to do it.

Thank you in advance-

---

### Post by Rui Pais on 2006-06-17
hi,
why do you delete your boot? I keep my boot that was made at my gentoo installation. 
Ubuntu only install the same grub... The only thing good is delete old or not needed kernels.

To install on MBR do 
```
sudo grub-install /dev/hda
```

check the Howtos here:
[https://wiki.ubuntu.com/GrubHowto](https://wiki.ubuntu.com/GrubHowto)
and
[https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows]("https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows")

---

### Post by rookee on 2006-06-17
Thank you for your reply!

I did what you told me, and..

```
root@ubuntu:/home/ubuntu #  grub-install /dev/hda
Probing devices to guess BIOS drives. This may take a long time.
/dev/mapper/casper-snapshot does not have any corresponding BIOS drive.

```

And regarding me deleting the boot, I didnt know that it would result in this! :( 

Any other suggestions?

---

### Post by Rui Pais on 2006-06-17
hi, you run those commands from a liveCD?
Do you mounted you /boot partition first? It may need the file /boot/grub/device.map.

check on 2nd link of previous post [this section]("https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows#head-778ecd20f83f92ebaa5aaec5f1b4615539c2f8d3").

---

### Post by rookee on 2006-06-17
Thats the thing, I dont have a /boot partition. All I have are the two fat32 windows partitions.

---

### Post by Rui Pais on 2006-06-17
Oh, 
to use Grub you should set a boot partition (with a grub folder and modules for filesystems and a menu.lst or a grub.menu file to gives you the menu). 

If you plan to use Ubuntu, just install Ubuntu (and you will get Grub). If you prefer to deal with it directly, use the Gentoo Handbook. It explain every detail of a manually grub installation.

If you just want to use windows you need to use some tool from Windows Repair disk that will recover the Windows booter.

---

### Post by kvonb on 2006-06-17
If you only want the windows partition to boot (no Linux at all), then boot from your Windows CD or floppy disk, drop to the command prompt and type:

fdisk /mbr

This will remove grub and make windows your ONLY booting OS.

If you install Linux again, it will setup grub for you.

Regards,

Kev :)

---

### Post by rookee on 2006-06-17
Done.

I arranged a 3GB partition (ext3) and installed Ubuntu (5.04) on it. I threw in Grub when it asked if I wanted it and after a reboot it still wouldnt work. I get [error 18](http://wiki.linuxquestions.org/wiki/GRUB#Error_18) when Grub tries to load and I have no idea what to do.

I seem to have a functioning Ubuntu installation but I cant run it. Im still on the Live CD. Can I chroot the the new installation (if so, how?) and try do something or should I just find a Windows CD and repair the MBR?

By the way, Rui Pais, congrats on the 2-0 victory.

Edit: Almost missed you, kvonb. I have tried this several times and I just cant reach the command prompt. I put in the disc, it tells me to "Press any key...", I get the blue installation screen and after that it makes me choose partition to install windows. I cant do anything in between. Several websites say that I should be able to repair MBR by pressing *R* at some point, but not even that I can do. Keep in mind that I dont have access to a floppy; im on a laptop, so a boot disk is out of the question.

---

### Post by Rui Pais on 2006-06-17
> **rookee]Done.

I arranged a 3GB partition (ext3) and installed Ubuntu (5.04) on it. I threw in Grub when it asked if I wanted it and after a reboot it still wouldnt work. I get [error 18](http://wiki.linuxquestions.org/wiki/GRUB#Error_18) when Grub tries to load and I have no idea what to do.[/QUOTE]
Hi, so now your problem seems to be the position of boot partition on disk. Too fazr away from the beginning of 1st sector of HD, probabily due to the size of window partitions. Is this happens when you have Gentoo on it (or you have a new partition scheme?

> 
I seem to have a functioning Ubuntu installation but I cant run it. Im still on the Live CD. Can I chroot the the new installation (if so, how?) and try do something or should I just find a Windows CD and repair the MBR?


A Gentoo  solution  said:**
> 
By the way, Rui Pais, congrats on the 2-0 victory.


Oh well, i don't care much with football (All neighborhood was screeming in the streets all afternoon, first on every gool then after the game :rolleyes: )  2 days ago a major portuguese [newspaper]("http://www.publico.clix.pt/shownews.asp?id=1261011&idCanal=57") bring the [data on european pib]("http://epp.eurostat.ec.europa.eu/pls/portal/docs/PAGE/PGP_PRD_CAT_PREREL/PGE_CAT_PREREL_YEAR_2006/PGE_CAT_PREREL_YEAR_2006_MONTH_06/2-15062006-EN-BP.PDF"). Portugal fall dawn from the 17º to the 18º position since last year. The year where us, one of the poorest country of Europe and with a very weak situation to invert that tendency, build almost 20 new stadiums just to have The World Cup (is how its called?) here. Now we have less investment in Wealth and worst in Education, cause, guess why, we don't have money!! :shock: I don't think we win :( 
(sounding too moralist... anyway thanks for the gentleness :))

---

