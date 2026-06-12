---
title: "Ubuntu 11.04 Won't Boot After Graphics Card Change"
date: 2011-06-30
forum: General Help
---

### Post by Jamesbug92 on 2011-06-30
Hi all!!
I have just had to change my graphics card due to the old one not working and ubuntu wont boot now. It just comes up with a blank screen, Windows Works Fine with the new card. 
Is it incompatable? (ATI Radeon 5450) 
Can anyone help or had the same problem?
Cheers 
James

---

### Post by coffeecat on 2011-06-30
I've used a Radeon HD 5450 card with 11.04 and it's fine with the default open source driver. You say you changed the card? What did you have before, and did you install a proprietary driver for it?

---

### Post by Jamesbug92 on 2011-06-30
before i had a MSI 6600v, I couldn't uninstall the driver as the graphics card went before i had a chance. I cant get onto ubuntu in recovory or normal.

---

### Post by dino99 on 2011-06-30
you should put back your old card, then boot on ubuntu, then remove xorg.conf or set it to use vesa, and close the system. 

Now put the new card in place and boot on ubuntu. Then set the graphic driver according to your card and activate it.

---

### Post by coffeecat on 2011-06-30
> **Jamesbug92 said:**
> before i had a MSI 6600v, I couldn't uninstall the driver as the graphics card went before i had a chance. I cant get onto ubuntu in recovory or normal.

The MSI card looks to be a nvidia. I'll have to assume that you installed the proprietary nvidia driver for this because you don't say. You say you can't boot into recovery mode? Please confirm. If so, this looks to be more than a video issue. You should be able to boot into recovery mode even with the "wrong" video card and driver.

I was going to suggest booting into recovery mode to uninstall the nvidia driver and remove xorg.conf, but if you can't then you would need to chroot into your installation from a live CD. Please confirm what happens with recovery mode and then we can take it from there.

---

### Post by Jamesbug92 on 2011-06-30
I cant put the old graphics card in as it does not work. And when booted in recovery mode it has lines going through the screenand is unreadable. I hope this helps 
James

---

### Post by coffeecat on 2011-06-30
Try this. I can't guarantee it will work, but it's the only thing you can do to purge the nvidia driver which may be interfering with the functionality of the ATI card.

Boot up a live Ubuntu CD or live USB. Go to the live desktop, not the installer. You need to know which is your Ubuntu partition. I'll assume it's sda5 for illustration, but you need to change this as appropriate. If you are not sure, post the terminal output (in the live session) of:

```
sudo fdisk -lu
```

Once you are in the live session, open a terminal, and:

```
sudo mount /dev/[COLOR="Red"]sda5[/COLOR] /mnt
```

I've reddened the bit you may need to change.

Now:

```
sudo mount -o bind /proc /mnt/proc
sudo mount -o bind /dev /mnt/dev
sudo mount -o bind /dev/pts /mnt/dev/pts
sudo mount -o bind /sys /mnt/sys
sudo chroot /mnt /bin/bash
```

You'll see that the prompt changes from '$' to '#'. You are now in your Ubuntu installation with root privileges. Take care what you type.

Now to uninstall the nvidia packages:

```
apt-get purge nvidia*
```

Rather bizarrely, this will take out ubuntu-desktop. Don't be alarmed - this is only a metapackage and can be reinstalled. It will also take out nvidia-common which is not causing any problem, but its removal will not be a problem if you are using an ATI card. Note that you don't need sudo in the chroot environment.

Now we need to disable xorg.conf:

```
mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

If you get an error, you have made a typo. Check capitalisation: it's capital-X, eleven.

That's it. Now:

```
exit
exit
```

That's correct - twice.

Now try to reboot into Ubuntu. What happens?

If you do manage to boot successfully into Ubuntu and Jockey (Additional Drivers) pesters you to install the proprietary driver for your ATI card - **ignore it**. At least for the time being. You may find the default open source driver more than adequate for your needs.

---

### Post by Jamesbug92 on 2011-07-09
Sorry For The Late Reply.
I Have tryed booting from a live CD and It will not boot it gets stuck with the multi coloured lines on the screen.
Thanks James

---

### Post by Jamesbug92 on 2011-07-19
Can Anyone Help ? Cant Boot From Live CD, USB Or The HDD To ubuntu ?

---

### Post by westie457 on 2011-07-19
If your motherboard has on-board graphics you could try resetting the bios to use that instead of the new one. Once you can log in to something the other suggestions will help you.

---

### Post by Wayne_V on 2011-07-19
It sounds like whatever graphics mode is set in your xorg.conf file is not compatible with the new card.   After boot, try <ctrl><alt><F1> and see if it switches to just a text mode login.

or, maybe you can ssh in from another system and remove/reinstall the graphics drivers 



You might get some more ideas here:

[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

---

### Post by Jamesbug92 on 2011-07-20
Ctrl, Alt F1 Didn't Do anything It Seems to crash when the lines pop up, i can accses all the ubuntu files using Windows And Puppy if thats any help? I have no on-board graphics but it was worth a try 
Thanks For your Help
This Comp Would Have Been Out The Window otherwise :D 
James

---

### Post by no2498 on 2011-07-20
? did you have all the lines with the old card also
if yes put it back in 
find a different monitor to try
i had two go  out at the same time monitor's that is

---

### Post by Jamesbug92 on 2011-07-20
I had no lines with the old graphics card but it is completly dead :(
I can try a different moniter now

---

### Post by no2498 on 2011-07-20
you may try pulling the systems battery out to reset the bios
on a side note i did this and the computer would Not take my pass word

---

### Post by Jamesbug92 on 2011-07-20
I Found A Old Nvidia Card In A Old PC I Put That In And It Ran Fine, I Did The Command Lines _**coffeecat **_Told Me To Do Then Shut Down And Put My ATI Card In And It Still Wouldn't Boot And It Had Multicolored Lines Going Through For About 20 Seconds Before Going To A Blank Screen Where The Monitor Goes Onto Standby Mode, CTRL, ALT, F1 Will Bring The Multicolored Screen Again. It Also Does This When Booting From A Live CD/USB, Pulling The CMOS Battery Did Nothing But Re-set The Time, Date And My BOIS Settings.
Is There Any Chance Of The Card Not Being 64Bit Compatible Or Anything Like That
Thanks Again 
James

---

### Post by Jamesbug92 on 2011-07-20
I Have Got It To Boot Using My ATI Card By Changing The "vt.handoff=7" In The Boot Line And Replaced It With "radeon.nonsense=1" (Something To Do With The Vesa Driver) , Once On I Installed The Driver It Popped Up Saying It Needed But Now It Won't Boot Again It Now Gets Stuck On A Black Screen With Only The Cursor.
Any Idea's 
Cheers 
James

---

### Post by wildmanne39 on 2011-07-21
Hi, you need to use nomodeset again, then you should be able to boot then you can see if you can find another driver for your card that works with it, if not you will have to make nomodeset permanent. Here is a link to help.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by lauchaxxx on 2011-09-03
Hi, Im kind of new on linux, not that new because I tried it several times, since RH6.1 and always go back to W for reasons like this.

Here is my new problem:

1- I installed ubuntu 11.04 and everything worked ok (with onboard nvidia vidcard).
2- Put another vid card (nvidia too)
3- Ubuntu didnt start (black screen)
4- then I removed the vid card
5- Ubuntu never stared again

It is stucked on GRUB.
any options that I chose got stuck in some place.

I have 5 options, none works.

ubuntu - generic
ubuntu - generic - safe
previous linux ver
memory test
memory test console (only this one works)

I only can get to my hard disk from a live USB.

can you guys help me?


thank you and sorry my english

---

### Post by JeremySchubert on 2012-01-14
CoffeeCat,
Thanks for this info.  I'm having an issue similar to Jamesbug92, except that I can boot in to the Live CD (version 11.10).  When I try to mount the appropriate partition (I'm assuming it should be 5 in my case) I get a message saying I save to include the file system type (which I assume is 'solaris' in my case).  But I don't know where to place the file system type in the command.  Can you please help me out.  I have included the 'sudo fdisk -lu output below.  
Thanks.

```

Disk /dev/sda: 20.5 GB, 20547841536 bytes
255 heads, 63 sectors/track, 2498 cylinders, total 40132503 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000361aa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    38037503    19017728   83  Linux
/dev/sda2        38039550    40130559     1045505    5  Extended
/dev/sda5        38039552    40130559     1045504   82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x08050804

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    78140159    39070048+   7  HPFS/NTFS/exFAT

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7d66b55a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048   976771071   488384512    7  HPFS/NTFS/exFAT

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7d66b5b8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1            2048   976771071   488384512    7  HPFS/NTFS/exFAT
root@ubuntu:/home/ubuntu# sudo mount /dev/sda2 /mnt
mount: you must specify the filesystem type
root@ubuntu:/home/ubuntu# sudo fdisk -lu

Disk /dev/sda: 20.5 GB, 20547841536 bytes
255 heads, 63 sectors/track, 2498 cylinders, total 40132503 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000361aa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    38037503    19017728   83  Linux
/dev/sda2        38039550    40130559     1045505    5  Extended
/dev/sda5        38039552    40130559     1045504   82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x08050804

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    78140159    39070048+   7  HPFS/NTFS/exFAT

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7d66b55a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048   976771071   488384512    7  HPFS/NTFS/exFAT

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7d66b5b8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1            2048   976771071   488384512    7  HPFS/NTFS/exFAT


```
> **coffeecat said:**
> Try this. I can't guarantee it will work, but it's the only thing you can do to purge the nvidia driver which may be interfering with the functionality of the ATI card.

Boot up a live Ubuntu CD or live USB. Go to the live desktop, not the installer. You need to know which is your Ubuntu partition. I'll assume it's sda5 for illustration, but you need to change this as appropriate. If you are not sure, post the terminal output (in the live session) of:

```
sudo fdisk -lu
```Once you are in the live session, open a terminal, and:

```
sudo mount /dev/[COLOR=Red]sda5[/COLOR] /mnt
```I've reddened the bit you may need to change.

Now:

```
sudo mount -o bind /proc /mnt/proc
sudo mount -o bind /dev /mnt/dev
sudo mount -o bind /dev/pts /mnt/dev/pts
sudo mount -o bind /sys /mnt/sys
sudo chroot /mnt /bin/bash
```You'll see that the prompt changes from '$' to '#'. You are now in your Ubuntu installation with root privileges. Take care what you type.

Now to uninstall the nvidia packages:

```
apt-get purge nvidia*
```Rather bizarrely, this will take out ubuntu-desktop. Don't be alarmed - this is only a metapackage and can be reinstalled. It will also take out nvidia-common which is not causing any problem, but its removal will not be a problem if you are using an ATI card. Note that you don't need sudo in the chroot environment.

Now we need to disable xorg.conf:

```
mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```If you get an error, you have made a typo. Check capitalisation: it's capital-X, eleven.

That's it. Now:

```
exit
exit
```That's correct - twice.

Now try to reboot into Ubuntu. What happens?

If you do manage to boot successfully into Ubuntu and Jockey (Additional Drivers) pesters you to install the proprietary driver for your ATI card - **ignore it**. At least for the time being. You may find the default open source driver more than adequate for your needs.

---

### Post by coffeecat on 2012-01-14
@JeremySchubert, you need to mount sda1, not sda5. In your case sda1 is your Ubuntu root partition and sda5 is your swap partition. You are getting a message asking for the filesystem type, because the mount command cannot recognise a swap partition. You do not use mount with swap. You won't need to specifiy a filesystem for sda1.

Is your problem the same as for the OP? My suggestions were specifically for a situation where the proprietary nvidia driver was interfering with an ATI card. If your situation is different, I suggest you stop now and post more details.

By the way, I've substituted code tags for quote tags for your fdisk output. You need code tags for terminal output in order to preserve formatting (and to avoid a wall of text).

---

### Post by JeremySchubert on 2012-01-14
Thanks @coffeecat.  I was assuming sda1 was my boot media (the CD).

My situation is that I had a nvidia card that stopped working.  So I replaced it with a card from another box.  When I try boot to graphical mode (normal mode???) I lose my monitor after the purple screen that says Ubuntu and has 4 dots.  I can boot into recovery mode and then drop to the root shell, so I know the monitor works.  So I figured the next step was to try remove the nvdia drivers and xorg.conf like your post suggests.  Let me know how that sounds to you.    
If that doesn't work, I don't mind re installing 11.10 using the option that 'al;lows me to keep my files but may remove system-wide settings'.  What would those system wide settings be?
Thanks, Jeremy

---

### Post by coffeecat on 2012-01-14
I follow your reasoning. The commands to remove the nvidia driver simply give you a system which will automatically load the appropriate open source video driver (all of which come in the box) when it boots up. What is the replacement video card? Is it nvidia, ATI or something else?

---

### Post by JeremySchubert on 2012-01-14
Here is what lspci reports.
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]

Funny thing is that I also have an on-board video port that doesn't but it doesn't seem to work.  I can't even find a setting for it in BIOS even though I can enable/disable the on board audio and nic. As an alternative can I install a PCI video card (if I can find one) so I can  go back to 2 monitors?  Or maybe it's just time to replace the whole computer :)
Thanks, 

Jeremy
```

00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:01.0 PCI bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE Host-to-AGP Bridge (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]
02:00.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (LOM) Ethernet Controller (rev 81)
```

---

### Post by coffeecat on 2012-01-14
> **JeremySchubert said:**
> Or maybe it's just time to replace the whole computer :)

Maybe! :wink:

That ATI card dates back to 2001 and a PC with only PCI slots is going to be difficult to furnish with a more up-to-date video card. The commands I posted all those months ago (but mounting sda1 instead) *should* get you a working system with the Radeon 7000 card, but let us know how you get on. 

Also - I mentioned in that post that purging the nvidia packages removes the ubuntu-desktop meta-package. If you get a working system with a GUI after running all those commands, I suggest you re-install ubuntu-desktop. It is only a meta-package and its absence will not affect the functionality of the system, except that without it you won't get updates for some of its dependencies.

---

### Post by matza55 on 2012-01-14
> **westie457 said:**
> If your motherboard has on-board graphics you could try resetting the bios to use that instead of the new one. Once you can log in to something the other suggestions will help you.

I have a HD5450- I'm using Ubuntu 11.10, and it works fine.

---

### Post by JeremySchubert on 2012-01-14
I'm up and running again, thanks for all the help!

Coffee Cat, I copied and pasted your commands into terminal.  is "-0" zero or the letter?

I will probably end up buying a replacement computer anyway.  As with Windows, I know that I'll have to do a fresh Ubuntu install.  But, is it possible to backup/copy my profile (or whatever the appropriate Ubuntu term is) so I don't have as much work to do setting up my desktop, printers, emails etc when the replacement computer is up and running?

Cheers,
Jeremy

---

### Post by coffeecat on 2012-01-14
> **JeremySchubert said:**
> 
Coffee Cat, I copied and pasted your commands into terminal.  is "-0" zero or the letter?

If you mean...

```
sudo mount -o bind /proc /mnt/proc
```

... and the rest, that's a lower-case o. Yes, copying and pasting commands into the terminal is always best.

> **JeremySchubert said:**
> But, is it possible to backup/copy my profile (or whatever the appropriate Ubuntu term is) so I don't have as much work to do setting up my desktop, printers, emails etc when the replacement computer is up and running?

Your personal settings are contained in various hidden folders and files in your home folder. If you have a separate home partition, it is possible to do a fresh install, keeping the old home partition. If you don't it is theoretically possible to copy various configuration files to your new home folder. The only config files I bother with for a new installation are those for my Thunderbird email client and irc client. The rest I find quicker and easier to re-configure from fresh - but that's a personal choice. I suggest you start a new thread when you are ready to re-install, detailing what you would like to carry over, and someone will be able to help you.

Good luck!

---

