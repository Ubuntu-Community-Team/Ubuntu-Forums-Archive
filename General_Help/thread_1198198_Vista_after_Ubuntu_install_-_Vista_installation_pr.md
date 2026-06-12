---
title: "Vista after Ubuntu install - Vista installation problem"
date: 2009-06-27
forum: General Help
---

### Post by cknight on 2009-06-27
A bit strange posting a Vista install question to a Linux forum!  Anyway, I need to re-install Vista on my system to upgrade the bios.  Using the Ubuntu live CD I've created space and NTFS formatted a primary partition for the Vista install.  However, when installing Vista, hitting 'Next' after selecting the partition on which to install it on, I keep getting the following error:
```
"Windows could not assign a drive letter to a partition on disk 0.  The error occured while preparing the computer's system volume.  Error code 0x80004005.
```


During the install process I've tried using Vista's disk utilities to delete and recreate the partition itself.  I've also dropped to a terminal (Shift F10) and used 'diskpart' to set the partition to active.  Nothing has made any difference.  Any ideas?  

For what it's worth, here's my fdisk output:
```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x20000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          62      497983+  83  Linux
/dev/sda2              63       33814   271112940    5  Extended
/dev/sda3           33815       38914    40957952    7  HPFS/NTFS
/dev/sda5              63        2129    16603146   83  Linux
/dev/sda6            2130       33316   250509546   83  Linux
/dev/sda7           33317       33814     4000153+  82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4ea93807

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641    5  Extended
/dev/sdb5               1       38913   312568609+  83  Linux

```

Rather frustrating that a dell supplied vista reinstall disk is so hard to use.

---

### Post by DeMus on 2009-06-27
> **cknight said:**
> A bit strange posting a Vista install question to a Linux forum!  Anyway, I need to re-install Vista on my system to upgrade the bios.  Using the Ubuntu live CD I've created space and NTFS formatted a primary partition for the Vista install.  However, when installing Vista, hitting 'Next' after selecting the partition on which to install it on, I keep getting the following error:
```
"Windows could not assign a drive letter to a partition on disk 0.  The error occured while preparing the computer's system volume.  Error code 0x80004005.
```


During the install process I've tried using Vista's disk utilities to delete and recreate the partition itself.  I've also dropped to a terminal (Shift F10) and used 'diskpart' to set the partition to active.  Nothing has made any difference.  Any ideas?  

For what it's worth, here's my fdisk output:
```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x20000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          62      497983+  83  Linux
/dev/sda2              63       33814   271112940    5  Extended
/dev/sda3           33815       38914    40957952    7  HPFS/NTFS
/dev/sda5              63        2129    16603146   83  Linux
/dev/sda6            2130       33316   250509546   83  Linux
/dev/sda7           33317       33814     4000153+  82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4ea93807

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641    5  Extended
/dev/sdb5               1       38913   312568609+  83  Linux

```

Rather frustrating that a dell supplied vista reinstall disk is so hard to use.

Before you continue: why do you need to have Windows to update your BIOS?
Which BIOS do you have? Isn't there a file you can download from the manufacturer's site and put it on a diskette, CD or even an USB stick and boot from there?
Read it first before you do all kinds of things, including damaging your Ubuntu installation.

---

### Post by cknight on 2009-06-27
> **DeMus said:**
> Before you continue: why do you need to have Windows to update your BIOS?
Which BIOS do you have? Isn't there a file you can download from the manufacturer's site and put it on a diskette, CD or even an USB stick and boot from there?
Read it first before you do all kinds of things, including damaging your Ubuntu installation.

The bios-flasher program provided by Dell is a windows exe file, and I believe reinstalling Vista directly to be the safest way to run this program.  I have  no idea what BIOS I have, but its for a Dell Studio 17 laptop.  By boot from a CD or USB, I assume you mean a linux boot from CD/USB?  This won't work for me as I need a windows environment to use this file.

---

### Post by DeMus on 2009-06-27
> **cknight said:**
> The bios-flasher program provided by Dell is a windows exe file, and I believe reinstalling Vista directly to be the safest way to run this program.  I have  no idea what BIOS I have, but its for a Dell Studio 17 laptop.  By boot from a CD or USB, I assume you mean a linux boot from CD/USB?  This won't work for me as I need a windows environment to use this file.

No, what I meant was, does the BIOS manufacturer (in this case Dell) have a file you can download and extract to a CD or USB stick with which you can boot your PC. In this case boot without real OS, just the disk or stick.
My BIOS has that. I put a file on a USB stick, reboot and the file starts running and updates the BIOS, all separate from the OS I have installed.
Maybe you can ask Dell.

---

### Post by kixome on 2009-06-27
why do you need to update the bios?

---

### Post by cknight on 2009-06-27
> **DeMus said:**
> No, what I meant was, does the BIOS manufacturer (in this case Dell) have a file you can download and extract to a CD or USB stick with which you can boot your PC. In this case boot without real OS, just the disk or stick.
My BIOS has that. I put a file on a USB stick, reboot and the file starts running and updates the BIOS, all separate from the OS I have installed.
Maybe you can ask Dell.
Heh, now that would be handy, but I doubt it.  From their website:
```
The file 1737_A06.EXE is using the Hard Drive format and is designed to be directly executed from Windows environments.
```

---

### Post by cknight on 2009-06-27
> **kixome said:**
> why do you need to update the bios?

I am having hardware issues (specifically, the multimedia keys have stopped working) and the dell support staff want me to upgarde the BIOS as a first course of action.

---

### Post by DeMus on 2009-06-27
> **cknight said:**
> Heh, now that would be handy, but I doubt it.  From their website:
```
The file 1737_A06.EXE is using the Hard Drive format and is designed to be directly executed from Windows environments.
```

Which website is this?

---

### Post by cknight on 2009-06-27
> **DeMus said:**
> Which website is this?

[http://support.euro.dell.com/support/downloads/download.aspx?c=uk&l=en&s=gen&releaseid=R224934&SystemID=studio1737&os=WLH&osl=en&deviceid=18343&devlib=0&typecnt=0&vercnt=4&catid=-1&impid=-1&formatcnt=1&libid=1&fileid=321952](http://support.euro.dell.com/support/downloads/download.aspx?c=uk&l=en&s=gen&releaseid=R224934&SystemID=studio1737&os=WLH&osl=en&deviceid=18343&devlib=0&typecnt=0&vercnt=4&catid=-1&impid=-1&formatcnt=1&libid=1&fileid=321952)

---

### Post by DeMus on 2009-06-27
> **cknight said:**
> [http://support.euro.dell.com/support/downloads/download.aspx?c=uk&l=en&s=gen&releaseid=R224934&SystemID=studio1737&servicetag=HBVMB4J&os=WLH&osl=en&deviceid=18343&devlib=0&typecnt=0&vercnt=4&catid=-1&impid=-1&formatcnt=1&libid=1&fileid=321952](http://support.euro.dell.com/support/downloads/download.aspx?c=uk&l=en&s=gen&releaseid=R224934&SystemID=studio1737&servicetag=HBVMB4J&os=WLH&osl=en&deviceid=18343&devlib=0&typecnt=0&vercnt=4&catid=-1&impid=-1&formatcnt=1&libid=1&fileid=321952)

Well, I have looked and also found no other BIOS file than the one you mention. Maybe you give them a call to find out, because it it seems so strange to have to have Windows installed just to get the BIOS updated.
Maybe the file you download is the same type of file I was talking about. Maybe also this one extracts to a CD with which you boot the computer to update the BIOS. Then you only would need Windows to extract the file. You don't have another computer, or maybe a neighbor who still uses Windows and who let you use his PC for a moment?

---

### Post by cknight on 2009-06-27
Well, thanks to those above who tried to help.  I finally found a solution.  Rather than trying to install Vista on my primary drive which had grub and Ubuntu, etc. already on it, I simply physically removed that drive from my laptop and installed Vista on my secondary hard drive.  This not only worked first time, but I didn't have to mess around reinstalling Grub afterwards.

The kicker of all this is that after finally getting Vista installed I don't need to upgrade the bios after all.  The act of removing the laptop battery, cover and/or harddrive somehow fixed my multimedia key problem.  Life's little ironies.

---

### Post by philcamlin on 2009-06-27
good to see its fixed

---

