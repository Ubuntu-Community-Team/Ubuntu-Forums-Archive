---
title: "busybox and initramfs"
date: 2011-06-06
forum: General Help
---

### Post by iamnigel on 2011-06-06
Hi fellow Ubuntu users.
 
Upon logging in, I get the GNU GRUB version list. Many options on the list have a recovery mode option. But no matter what option I pick, I get a black screen that reads,
 
"Busybox v1.15.3 (Ubuntu 1:1.15.3-1ubuntu5) built-in shell (ash)
Enter 'help' for a list of built-in commands.
 
(initramfs)"
 
Please, please, please help. I have so many important files.

---

### Post by mocoloco on 2011-06-07
Sounds like your Grub2 is messed up, you could try re-installing it.  Boot from a liveCD and follow [these instructions]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2").

---

### Post by linuxinstalledfromhdd on 2011-06-07
If they aren't in a hurry they can wait around for a couple of the users here that know how to fix grub2 issues..

Otherwise, you can boot from a live disc, install to resize your partitions, and reinstall Ubuntu.  Use 10.10 just to be on the safe side.  And migrate your data over to the new installation, and then resize your old partition to zero when you are done. 

Here is a guide to get you up and running again quickly after you do that:

[http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/](http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/)

Or....  You can wait for someone who -may- be able to untangle your Grub issues.

---

### Post by iamnigel on 2011-06-07
I have a new computer, so all I care about is retrieving my files from my old computer that has the initramfs prompt, and moving the files from the old computer to my new computer.
 
I don't know how to handle the Grub2 thing, and I have been googling all night.

---

### Post by vivek.pandey on 2011-06-07
check out this link 
[http://ubuntuforums.org/showthread.php?t=1729059&page=3](http://ubuntuforums.org/showthread.php?t=1729059&page=3)

---

### Post by matt_symes on 2011-06-07
Hi

You can get dropped to the busy box prompt for a number of reasons and we may be able to boot you into Ubuntu depending on what the issue is that is causing you to drop to busybox.

First things first. 

What version of Ubuntu are you using ? 
What other operating systems do you have on you PC ?

The first thing i would try at the busy box prompt is to type

```
exit
```

If the system can, it will try to continue the boot sequence. Does this continue the boot sequence ?

If not then type

```
blkid
``````

```

Take a picture of the screen with a camera (phone) and post the results back here. 

Depending on the problem we may be able to continue the boot sequence.

Kind regards.

---

### Post by iamnigel on 2011-06-08
A picture of the screen is attached.
 
Typing "exit" doesn't work.
 
I am using Ubuntu 10.10 and have no other operating systems on my computer, although I did attempt to install Windows XP several months ago and failed.
 
Thank you guys for your help.

---

### Post by Rubi1200 on 2011-06-08
Hi and welcome to the forums :-)

The best thing to do right now so we can help you troubleshoot this is to do the following please:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script which is in a zipped file. There is a link in my signature.
2. Once downloaded, move the boot info script by either copying or dragging and dropping the zipped folder onto the desktop and unzip the contents by using right-click Extract here.
3. Open the folder and copy the script to the desktop (you can also drag and drop if you like)
4. Open a terminal and run the following command

```
sudo bash ~/Desktop/boot_info_script.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by linuxinstalledfromhdd on 2011-06-08
[http://cinderbox.net/2011/06/08/how-to-fix-grub-grub2-windows-mbr-and-lost-systems/](http://cinderbox.net/2011/06/08/how-to-fix-grub-grub2-windows-mbr-and-lost-systems/)

---

### Post by iamnigel on 2011-06-08
These are the contents of the RESULTS.txt:

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sda.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdb and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for (,msdos1)/boot/grub.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 2011-04-18
    Boot sector info:   Syslinux looks at sector 8026 of /dev/sda1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1051 MB, 1051721728 bytes
33 heads, 61 sectors/track, 1020 cylinders, total 2054144 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             61     2,053,259     2,053,199   c W95 FAT32 (LBA)


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048   306,440,191   306,438,144  83 Linux
/dev/sdb2         306,442,238   312,580,095     6,137,858   5 Extended
/dev/sdb5         306,442,240   312,580,095     6,137,856  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        07F0-3C1A                              vfat       PENDRIVE
/dev/sdb1        ed80035d-c1f9-45fc-8272-118ae9fa1225   ext4       
/dev/sdb5        29368b0b-e0a3-49e6-aeb1-5828560ec95a   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


========================= sda1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
--------------------------------------------------------------------------------

================= sda1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sda1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

/home/ubuntu/Desktop/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

---

### Post by iamnigel on 2011-06-08
This is the RESULTS.txt in code form, like you asked. Sorry to have two long posts like this. I didn't understand you instructions the first time. :/

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sda.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdb and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for (,msdos1)/boot/grub.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 2011-04-18
    Boot sector info:   Syslinux looks at sector 8026 of /dev/sda1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1051 MB, 1051721728 bytes
33 heads, 61 sectors/track, 1020 cylinders, total 2054144 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             61     2,053,259     2,053,199   c W95 FAT32 (LBA)


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048   306,440,191   306,438,144  83 Linux
/dev/sdb2         306,442,238   312,580,095     6,137,858   5 Extended
/dev/sdb5         306,442,240   312,580,095     6,137,856  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        07F0-3C1A                              vfat       PENDRIVE
/dev/sdb1        ed80035d-c1f9-45fc-8272-118ae9fa1225   ext4       
/dev/sdb5        29368b0b-e0a3-49e6-aeb1-5828560ec95a   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


========================= sda1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
--------------------------------------------------------------------------------

================= sda1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sda1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

/home/ubuntu/Desktop/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected


```

---

### Post by Rubi1200 on 2011-06-08
Hi,
there seems to be damage to the file-system on sdb1 where Ubuntu is installed.

Did you do a hard shutdown,, battery died, power outage or something similar?

In any event, to fix this you need to run the following command from a LiveCD:

```
sudo e2fsck -f -y -v /dev/sdb1
```Once the command completes, and assuming no errors, reboot taking out the CD and you should be back in Ubuntu.

Let me know how things work out.

---

### Post by iamnigel on 2011-06-08
Thank you so much, Rubi1200! You are my hero! My savior! I had 2,000 songs and was writing a freaking book. I was going to lose so much. I cannot thank you enough.

---

### Post by Rubi1200 on 2011-06-08
> **iamnigel said:**
> Thank you so much, Rubi1200! You are my hero! My savior! I had 2,000 songs and was writing a freaking book. I was going to lose so much. I cannot thank you enough.
Excellent! I am really pleased this worked and you can access your data again :D

Please do yourself a favor and make backups to an external medium. The cost of an extra drive far outweighs the pain of losing so much important stuff.

The last favor you can do, and it will be thanks enough, is to mark this thread Solved using the Thread Tools near the top of the page.

Good luck with your book.

---

### Post by Jimcamera on 2011-06-09
Hello,

Am I able to hijack this thread?  I have exactly the same problem.  I posted previously but had no replies, - this thread seems to have more potential.  I do apologise if I'm breaching netiquette here, and feel free to chastise me...

So, to sum up, I too have the busybox/initramfs problem.  I have been able to boot up using a 10.10 live cd (though not my original 10.04 live cd, which is curious).  Using some of the disk utilities within this I see that I cannot access the part of the drive partitioned for Ubuntu - during a system test, for example, it runs disk bench forever, and from 'Places', I cannot access the drive.

I have followed the instructions outlined above, and please find attached the photos.

I do hope someone can help me, thanking you in advance...

All the best

Jim

---

### Post by Jimcamera on 2011-06-09
Hello again, thread hijacker here...

For some reason, my thread hadn't updated, so I hadn't seen all the extra information beyond post number six or so.  I will study this and see what I can do with that.

Thanks.

Jim

---

### Post by Rubi1200 on 2011-06-09
Hi and welcome to the forums Jimcamera :)

You are right, the staff do not appreciate thread hijacking. The other problem is that even if it seems your problem is the same or similar, it usually is not.

Therefore, please go back to the thread you started a few days ago (and where I posted a response) and follow the instructions there.

Thanks.

---

### Post by Jimcamera on 2011-06-09
Thread hijacker yet-again.  Looks like my images didn't get through, so I'll try sending them with this.  

In the meantime, I have followed the instructions regarding boot_info_script and it is running but is currently hanging, and has been for about ten minutes now.  It reads:

"gawk" could not be found, using "busybox awk" instead.
This may lead to unreliable results.
[I]
Identifying MBRs...
Computing Partition Table of /dev/sda...
Searching sda1 for information...
Searching sda2 for information...
Searching sad3 for information...
Searching sda4 for information...
Searching sda5 for information...[/I]

And that's where it hangs.  This would seem to echo the issues I discovered with my system testing.


Thanks!

Jim

---

### Post by Jimcamera on 2011-06-09
Just seen your message, Rubi2000. Obviously, my thread management leaves something to be desired.  I will start from my original post from scratch.  See you there.

Sorry for any misdemeanours, bollocking accepted.

Best

Jim

---

### Post by spikoley on 2011-07-02
> **Rubi1200 said:**
> Hi,
there seems to be damage to the file-system on sdb1 where Ubuntu is installed.

Did you do a hard shutdown,, battery died, power outage or something similar?

In any event, to fix this you need to run the following command from a LiveCD:

```
sudo e2fsck -f -y -v /dev/sdb1
```Once the command completes, and assuming no errors, reboot taking out the CD and you should be back in Ubuntu.

Let me know how things work out.

This worked for me.  Thanks!

---

### Post by Rubi1200 on 2011-07-03
Hi spikoley,
glad this solution also worked for you :-)

---

