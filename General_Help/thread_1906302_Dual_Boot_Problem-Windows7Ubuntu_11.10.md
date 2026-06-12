---
title: "Dual Boot Problem-Windows7/Ubuntu 11.10"
date: 2012-01-08
forum: General Help
---

### Post by Rag888 on 2012-01-08
Ok, I am absolutely new to Ubuntu, but after wasting almost 2 days have earned enough know how to play with the OS. So I installed Ubuntu with wubi thingy and when I was trying to install softwares (not made for Ubuntu) with WINE I found out that the installation procedure gave me the error regarding the file being unsafe and that it cannot recognize it. So I searched your forums and found out that the problem was with the 'Permission' of file to let it an 'executable'.

The solution was pretty simple that one should just go to the properties of the file and change the permission to 'all to executable', but that did work out for me i.e. whenever I would try to 'tick/check' the executable part the 'tick' would remove itself automatically.

I also found a few solutions for this new problem, but it didnt work out for me. Then I stumble upon another solution that one should first copy the file to the 'Home' folder of Ubuntu and then it would allow me to change the permissions, and guess what it worked!!

So I installed quite a few programs until while trying MS Office 2007 I found out that I was presented by a new error regarding my disk space being low. I again searched for it and found out that only 3 GB of space was allotted for Ubuntu although during the Wubi install I had changed the destination partition from 'C' (windows partition) to 'E' empty partition.

Anywaz, the only solution I found workable to '[B]migrate wubi install to partition', so I decided to do it. I took help from this thread of yours:
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

But during the procedure I received an error that the destination partition has to be formatted in Linux format. So searched a bit more and found the way to do it.

I used 'GParted' to format the 'D' drive (an empty partition) in the 'ext4' format and succeeded and then i 'migrated' the wubi install to it. It again was successful.

I restarted by laptop and all worked fine, it showed me both the options at Boot (whether to go inti Ubuntu or Windows 7). I then installed a few chat clients (Pidget, Gyati etc), but didnt find them suitable so I removed them and settled with 'Empathy' (it was already installed).

And then I was done with it I decided to shut down my Laptop but befor that thought it would be a good idiea to login to Windows to see if the things were alright. So when i restarted the laptop, to my utter surprise the pc directly booted into Ubuntu without giving me the boot secreen, and just showed me the GRUB screen with the options of Ubuntu, Ubuntu previous version, Ubuntu recovery, and some memory tests.

I was stoned!!

But to my luck after a little search I found out that by using the following command the problem may be solved:

 [/B]sudo update-grub

So I used it in the terminal and voila, the GRUB started showing me the Windows Loader thing in the option in addition to Ubuntu.

So I prayed and booted into windows and after some black/blank screens I successfully logged into Windows, and man that was a relief!!

I happy, and I am thankful to the gurus on this forum for their help (though the sudo update thing I found from some other website :)).

Now this brings me to my actual question (I gave the history so that others can learn a lesson that being a noob one should not try to act smart :D), is that how can I go back to the same Boot Options that were there when when everything was alright i.e. you turn on the PC and the black screen comes up showing you the 2 options with a timer i.e. Ubuntu and Windows 7 and from there you can choose which OS you want to log into.

Though I am booting fine into both the OS', but the issue is that you turn the PC on, it will straight away go to the GRUB screen, from there it will show you the boot options, you would then select Windows Loader sda1 and then again the black screen will appear with the timer asking me to choose between Ubuntu or Win 7 and then when I select Win 7 it would take me to windows.

I just want to make it right and normal.

Thanks in advance.

P.S Sorry for the long post, I just wanted to share the entire thing, may be this will save others.

---

### Post by Rag888 on 2012-01-08
_**Here's the Boot Info of my Laptop**_:



                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       733,183       731,136   7 NTFS / exFAT / HPFS
/dev/sda2             733,184   164,120,575   163,387,392   7 NTFS / exFAT / HPFS
/dev/sda3         164,120,576   532,760,575   368,640,000  83 Linux
/dev/sda4         532,760,576 1,250,260,991   717,500,416   f W95 Extended (LBA)
/dev/sda5         532,762,624   901,402,623   368,640,000   7 NTFS / exFAT / HPFS
/dev/sda6         901,404,672 1,250,260,991   348,856,320   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        9C3262103261F026                       ntfs       System Reserved
/dev/sda2        76DC66F9DC66B2D3                       ntfs       
/dev/sda3        d6541e2a-d657-440e-88bc-8a5a0d6bb193   ext4       
/dev/sda5        7A943C41943C01E5                       ntfs       New Volume
/dev/sda6        1C120367120344EC                       ntfs       Back Up

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /tmp/BootInfo0/sda1      fuseblk    (ro,nosuid,nodev,allow_other,blksize=4096)
/dev/sda3        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda6        /media/Back Up           fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


========================== sda1/grldr embedded menu: ===========================

--------------------------------------------------------------------------------

=============================== StdErr Messages: ===============================

unlzma: Decoder error
/home/otichi30/Downloads/boot_info_script.sh: line 1888: (  / 2 ) + 16 : syntax error: operand expected (error token is "/ 2 ) + 16 ")

---

### Post by Mark Phelps on 2012-01-09
Sounds like what you want, now that you have Ubuntu installed in a separate partition, is to go back to using the Windows boot manager to do the selection, right?

If that is the case, what you would need to do is the following:
1) Remove GRUB from your MBR -- you can do this by booting from a Win7 Repair CD and running Startup Repair (may need to do this three times), using Boot-Repair (in Ubuntu) to rewrite the MBR, or (inside Win7) using EasyBCD to rewrite the MBR.
2) Once the MBR has been rewritten, your PC will automatically boot into Win7. Is this what you want?
3) You can then use EasyBCD to add an entry to the Windows bootloader for Ubuntu -- the details for doing this are on the NeoSmart Technologies forum (providers of EasyBCD)
4) Once you update the Windows BCD with EasyBCD, when you reboot, you will get a Windows menu -- with entries for Windows and Ubuntu.

---

### Post by Rag888 on 2012-01-09
Thanks for you reply.

I wanted that I should be presented with windows boot manager (the black window giving me the options to whether boot into Windows or Ubuntu).

Point to be noted is that I can still boot into the both the OS, but the difference is that instead of the Window Boot Manager Showing up BEFORE the GRUB, I am presented with the GRUB FIRST, and then I selecet windows Loader (sda1) it takes me to the windows boot manager with the choice of booting either windows or ubuntu.

Anyhow, I have fixed it, using the bootcect.exe command in the after loaded a Windows DVD as per the procedure explained here:

[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

Now I am first shown the windows boot manager and then when I select Ubuntu, it will take me to GRUB.

---

### Post by Rag888 on 2012-01-10
Should the laptop show the GRUB first or the windows boot manager first?

---

### Post by Mark Phelps on 2012-01-11
> **Rag888 said:**
> Should the laptop show the GRUB first or the windows boot manager first?

If GRUB is installed to the MBR, the laptop will attempt to boot to the Linux filesystem that GRUB points to, and if there is more than one OS on the PC, you will see a GRUB menu.

If you're still getting a GRUB menu, then GRUB was NOT removed from the MBR.  If you want it removed, then follow the instructions I provided in my post.  When it's gone, you will NOT get a GRUB menu anymore.

---

