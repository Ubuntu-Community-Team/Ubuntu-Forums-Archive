---
title: "Can't boot into XP on dual boot system"
date: 2010-10-04
forum: General Help
---

### Post by rayzorx on 2010-10-04
Hi all,
I hope someone can advise me on how to resolve this or point me to a good document.

I have an eMachines PC that had Ubuntu 10.4 on disk one  and WinXP on disk two. (My wife uses the XP for some old programs) Yesterday, the PC motherboard died, and my wife is concerned about getting her data off of the XP disk. 
I got an old PC from a friend and installed my 2 drives in it, with the intent to boot to XP and off load my wife's data.

I've got the cables connected so that I boot up to the Grub  menu, and I can boot into Ubuntu fine.  However, when I select the Windows option, I come up to the screen that says something to the effect that Windows ended abnormally and it gives you options to boot Normally, or in Safe Mode, Safe Mode with Network, etc.

No matter which option I pick, it just loops back around and gives me an error 17.  So I can't boot into Windows.

I have a suspicion that maybe the boot loader doesn't see the XP drive at the correct location(?) but I'm not sure. 

Any help is greatly appreciated!
Ray

---

### Post by wilee-nilee on 2010-10-04
Can you get into XP from Ubuntu. You migt try a chkdsk /r from the command line in the f8 safe mode. This will just trigger a chkdsk at restart.

If you need a XP ISO for repairs here is one.
[http://www.aspireoneguide.com/xpinstallu3.html](http://www.aspireoneguide.com/xpinstallu3.html)

I have used this link with legit OEM keys to activate, it is not locked to acer.

---

### Post by Tr0w4Tr3y on 2010-10-04
I think thats the best idea, to mount your XP disk and explore it with your ubuntu. That is one of XP's problem, you can't just put it in another PC because of the hardware configuration will have a conflict on the system and just continued to restart or BSOD. Just copy the files that you need and reformat it if you want.

---

### Post by oldfred on 2010-10-04
When I put a new motherboard in my system, XP wanted to call BillG to confirm that it was ok. The internet screen to go to microsoft was behind the login/error menus/screens and unless I clicked on the internet check first it would not go any further. I could not see that screen until I dragged the overlay screens around.

---

### Post by smilodonis on 2010-10-04
I would recommend to use a simple Ubuntu Live CD/DVD, boot up and simply copy the selected documents or do a backup. Format type is not an issue, just did a full NTFS backup from XP and Vista machine.

---

### Post by rayzorx on 2010-10-05
> **Tr0w4Tr3y said:**
> I think thats the best idea, to mount your XP disk and explore it with your ubuntu. That is one of XP's problem, you can't just put it in another PC because of the hardware configuration will have a conflict on the system and just continued to restart or BSOD. Just copy the files that you need and reformat it if you want.

OK, so I was able to mount my XP drive from my Ubuntu and I can do an ls in my /mnt/winxp dir and see the windows dirs and get my files.  Now is there a fix for my Grub loader so I can boot to the windows drive again?

---

### Post by oldfred on 2010-10-05
The windows boot loader when it is in the MBR just jumps to the PBR or partition boot sector flagged as the active partition (boot flag) to continue to boot. All grub does is bypass the MBR and jump to the windows PBR. If you get windows to start to boot then it is not a grub issue but a windows issue.

You can post this:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by searchfgold6789 on 2010-10-05
The windows MBR might be just fine and dandy, since you didn't appear to do anything to it at all...
You could be having trouble just with hardware drivers for windows!!!!!

---

### Post by rayzorx on 2010-10-05
> **oldfred said:**
> The windows boot loader when it is in the MBR just jumps to the PBR or partition boot sector flagged as the active partition (boot flag) to continue to boot. All grub does is bypass the MBR and jump to the windows PBR. If you get windows to start to boot then it is not a grub issue but a windows issue.

You can post this:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

Good Tip!  Thanks!!
I ran bootinfoscript and got the Results file.  In looking at it I noticed that there was no entry for the WinXP HD in my fstab file.  Thinking that maybe my Window MBR was hosed, I ran TestDisk, per instructions at SourceForge.net.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

I followed these steps:
First   screen:  Select "No Log" and press enter.
  Second  screen:  Select the hard drive containing  the Windows system partition and  choose "proceed".
  Third   screen:  "intel"
  Fourth  screen:  "advanced",
  Fifth   screen:  Select the Windows system partition  and choose "boot"
  Sixth   screen:  "BackupBS"
  Seventh screen:  type "Y" to confirm

Screen 5 my output is this:

Disk /dev/sda - 61 GB / 57 GiB - CHS 7476 255 63

     Partition                  Start        End    Size in sectors
 1 * HPFS - NTFS              0   1  1  7474 254 63  120085812




[  Type  ]  [  Boot  ]  [  Quit  ]
                              Boot sector recovery

Screen 6 is this:


TestDisk 6.8, Data Recovery Utility, August 2007
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 61 GB / 57 GiB - CHS 7476 255 63
     Partition                  Start        End    Size in sectors
 1 * HPFS - NTFS              0   1  1  7474 254 63  120085812

Boot sector
Status: OK

Backup boot sector
Status: OK

Sectors are identical.

A valid NTFS Boot sector must be present in order to access
any data; even if the partition is not bootable.

[  Quit  ]  [  List  ]  [Rebuild BS][Repair MFT][  Dump  ]
                            Return to Advanced menu


I don't see the BackupBS option so I selected Rebuild BS. 

This is the output:
Disk /dev/sda - 61 GB / 57 GiB - CHS 7476 255 63
     Partition                  Start        End    Size in sectors
 1 * HPFS - NTFS              0   1  1  7474 254 63  120085812

filesystem size           120085812
sectors_per_cluster       8
mft_lcn                   786432
mftmirr_lcn               16
clusters_per_mft_record   -10
clusters_per_index_record 1
Extrapolated boot sector and current boot sector are identical.

[  Dump  ]  [  List  ]  [  Quit  ]

                           List directories and files


So I'm not sure if this did anything.  I'm going to reboot the system and see if it can start Windows. I'll post results.

Ray

---

### Post by rayzorx on 2010-10-06
Well all this didn't change anything, so I'm still backing up all the data I can get off of the WinXP disk before I try anything else.  Oh yeah, I cd to /mnt/winxp/ system\ volume \information and do a dir, and I see this:

rayzorx@Ubuntu1:/mnt/winxp$ cd  System\ Volume\ Information
rayzorx@Ubuntu1:/mnt/winxp/System Volume Information$ dir
MountPointManagerRemoteDatabase			tracking.log
_restore{4C6E9B3C-F1BE-4527-8708-5AE69FD346FA}

is there something in here that may help me?  Like the restore file?

 Any suggestions??

---

