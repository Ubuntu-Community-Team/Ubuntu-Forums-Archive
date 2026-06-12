---
title: "Difficulty making installation CD/USB"
date: 2011-11-23
forum: General Help
---

### Post by Paperypip on 2011-11-23
I've recently assembled a new PC and decided I would like to try dual-booting Windows 7 and Ubuntu 11.10. I downloaded the .iso of the 64-bit version of Ubuntu 11.10 and checked the md5 sum ([62fb5d750c30a27a26d01c5f3d8df459 as it should be according to the website]("https://help.ubuntu.com/community/UbuntuHashes")) burned it to a CD using ImgBurn. My optical drive is a Samsung SH-B123L with the firmware updated to the most recent version. When I tried booting from it, I got to a screen that gave me the message 

```
(initramfs) Unable to find a medium containing a live file system
```

I double-checked that my md5 was good and figured it must have been a bad burn. Tried burning discs again a few times and got the same result. Just now I tried running ImgBurn's verify tool on the most recently burned of these discs against the original, good .iso and got a huge amount of miscompares:

```

I 20:10:04 Verifying Session 1 of 1... (1 Track, LBA: 0 - 357013)
I 20:10:04 Verifying Track 1 of 1... (MODE1/2048, LBA: 0 - 357013)
W 20:10:13 Miscompare at LBA: 799, Offset: 57, File: \casper\initrd.lz
W 20:10:13 Device: 0x24
W 20:10:13 Image File: 0x2C
W 20:10:13 Total Errors in Sector: 1
I 20:10:13 Verifying Sectors...
W 20:10:18 Miscompare at LBA: 968, Offset: 689, File: \casper\initrd.lz
W 20:10:18 Device: 0xA3
W 20:10:18 Image File: 0xA7
W 20:10:18 Total Errors in Sector: 1
I 20:10:18 Verifying Sectors...

```

(plus a whole lot more that looked a lot like that)

So I seem to quite consistently be burning bad Ubuntu discs. I don't really have any idea how I might diagnose precisely what's happening.

---

After the CD stuff didn't work I decided to try to make a bootable USB instead. I used [the Universal USB Installer]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3") to put the image file (checked the md5 once again before I did this just to be extra sure) on my Kingston 4gb USB stick (only USB stick I have lying around here) and it seemed to work. I tried booting from it and got to the screen where you have the options to try Ubuntu, install, check memory, etc. However, if I tried to try Ubuntu or install I'd get a message something like this:

```

Kernel Panic-not syncing: VFS: unable to mount root fs on 
unknown block(8,1)

```

I'm still trying things but that's the main thrust of my difficulties. I don't know whether they're related, but mainly I cannot make either a CD or a USB from which I can install Ubuntu.

---

### Post by rokytnji on 2011-11-24
For the cd. It might be the make of cd that is at fault. Like Memorix or whatever. Try a different CD brand maybe. Also Burn CD as slow as possible in Image Burn. If you can use 4x. That is good.

For the USB. Make sure to reformat the kingston (I have a few data travelers) in Windows with 
[http://files.extremeoverclocking.com/file.php?f=197](http://files.extremeoverclocking.com/file.php?f=197)
first (fat32). Then try your installer (Lili I am guessing)

I don't use Windows on my gear so Unetbootin works for me in Linux (I run AntiX mostly). They have a Windows version also. 

Good Luck.

---

### Post by Paperypip on 2011-11-24
Tried using DVD-RWs instead to no success. Tried three different installers for the USB- Pendrive, Lini, and Unetbootin. None work.

This page - [https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization) - refers to the "(initramfs) Unable to find a medium containing a live file system" error in a similar context to mine. It suggests something is failing to mount but I'm too much of a novice to tell whether that's useful information for my problem. :(

---

### Post by Paperypip on 2011-11-25
Semi-success! Today I got my laptop back from the repair shop. I tried burning a CD on the laptop- md5 was good, no disc verification errors (What does it mean that I was getting so many errors of that sort on my desktop? Kind of worried now). I got the exact same error after booting that I previously described:

```
(initramfs) Unable to find a medium containing a live file system
```Then I tried creating a bootable USB from the laptop instead and then tried booting from it at the desktop. It worked! Currently I'm installing Ubuntu. I'm kind of still worried about the issue I was having though- what if they're indicitive of some underlying problem that I haven't fixed?

---

### Post by hansdown on 2011-11-25
Welcome to the forum, Paperypip.

Glad you got it working, good job.

The problem with the discs could be; Burning at more than 4x speed.

The slower the burn, the less chance of corruption.

Glad you stuck it out, and fixed it.

---

### Post by Paperypip on 2011-11-25
Hmmmm, when I load up an empty CD in ImgBurn on my desktop it says the lowest supported burn speed is 16x and if I do the same on my laptop, it says the lowest burn speed is 10x. I was aware I should be using as low a speed as possible but I wasn't aware 4x was considered too fast. Could that have anything to do with it? If I tried to set it lower it would tell me that speed is unsupported and it would use the slowest supported speed instead.

I'd say if burn speed was the issue and I don't have support for a slow enough burn speed on the computer at all, that problem could probably be written off as a quirk of the specific hardware I have. I'm still curious about the issues with the USB though...

---

### Post by hansdown on 2011-11-25
4x is o.K.

It's a software issue, if you can't burn at 4x, or less.

Sorry, I didn't pick up, on the USB issue.

O.K., Re-read your first post.

Glad you fixed it. :D

---

### Post by Miljet on 2011-11-25
It is also possible that your CD/DVD problem could be either a dirty lens on the drive or a faulty drive. If I start having problems with an optical drive, I just replace it since they are so cheap now.

---

### Post by hansdown on 2011-11-25
> **Miljet said:**
> It is also possible that your CD/DVD problem could be either a dirty lens on the drive or a faulty drive. If I start having problems with an optical drive, I just replace it since they are so cheap now.

Also, a good call.

Thanks, Miljet.

---

### Post by Paperypip on 2011-11-25
Okay, I'll look into possible issues with my optical drive then. It's brand new so if there's issues I shouldn't have too much trouble getting it replaced under warranty. Thanks everyone.

Just booted into Ubuntu off my desktop's SSD for the first time, looks like installation was successful. :D

---

