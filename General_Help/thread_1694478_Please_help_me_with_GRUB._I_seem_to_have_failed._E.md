---
title: "Please help me with GRUB. I seem to have failed. Epicly."
date: 2011-02-24
forum: General Help
---

### Post by reallybadwithlinux on 2011-02-24
Hey guys. So I'm really new to Ubuntu, so please treat me like a child. I decided to install Ubuntu the other day when I got bored. After it installed, I had a GRUB boot menu that worked perfectly, however something must have been wrong with my installation as it didn't boot. I didn't really care, but since the partition used to installed ubuntu was like 40GB, I tried to get the space back. So I booted to windows and in the partition manager I formatted the Ubuntu partition. Or I think I did. This is what's quite weird. The partition still seems to exist, but I had completely lost the GRUB menu and on boot my computer went to GRUB rescue. There seems to be something wrong with my disc drive so the only thing I can boot from is a USB stick.
I then used UNetbootin to launch into Ubuntu. I figured the problem would be solved if I just did a complete reinstall of Ubuntu. But the installation always hangs. I later found out that it hangs when scanning my disks, so there's likely something effed up there. 
So I decided that if I could just get GRUB to work, then I'd at least be able to boot back into Windows and worry about the rest of this crap later (I'm supposed to be on a holiday). So I followed some instruction and reinstalled GRUB from a USB copy of Ubuntu. 
So, here's where I'm at now. When I boot my computer, it leads straight to the GRUB 1.98 command line. How do I boot to windows from here? And I'm looking for ANY solution here. I'm completely ready to get rid of Ubuntu, may just use wubi next time :D

Sorry the post is so long guys, I really appreciate any help.

---

### Post by YesWeCan on 2011-02-24
Hi there. I can predict that you are not "really bad with linux" but rather you are not skilled with Grub. But not too worry, this forum is rife with highly intelligent people who can't figure out what the heck grub is doing and how to use it.

I don't blame you for wanting to abandon Ubuntu at this point. Especialy if you are worried about how to get Windows to boot again.

Have you got your Windows CD? The best thing is to boot of this and use it to reinstall the Windows boot loader. Then you'll be all Windows again. :)

What you didn't know is that Grub has some of its files inside the Ubuntu partition. So when you deleted the partition grub could not find its menu and so could not offer to boot Windows. The least calamity prone method is to install Ubuntu with grub on its own disk, so that nothing is touched on your Windows disk. That way, you can always boot Windows as normal if you need to and you can abuse Ubuntu as much as you like without fear of screwing up your Windows boot. . This may not be an option for you, I don't know.

---

### Post by reallybadwithlinux on 2011-02-24
Hey, thanks for your reply. I have a windows cd, but there seems to be something wrong with my cd tray. In bios I told the computer to give the cd drive first boot priority, but the drive is very very very rarely detected (I've booted like a hundred times over the past day and only successfully booted to disc twice. This was with my ubuntu live disc and became the reason I had to resort to USB). I'm not sure if this is a hardware error or not. I've done some searches for the symptoms I have and I've discovered some similar stories with the cd drive, but I never found a solution.

---

### Post by bcbc on 2011-02-24
Boot from your Ubuntu install medium (cd/usb) and select "Try Ubuntu" or "Try without installing". This will boot in 'live CD' mode.

Then go to a terminal (CTRL+ALT+t) and run the following:
```
sudo apt-get install lilo
```
You'll see a popup panel with lots of warnings - which are safe to ignore as they relate to booting linux, not windows - so TAB to OK and hit ENTER. Then run:

```
sudo lilo -M /dev/sda mbr
```

This installs a windows-like version of the lilo bootloader. Reboot into Windows.

---

### Post by bcbc on 2011-02-24
If you can boot your windows DVD or repair CD, then you can also use these to boot to a repair prompt and run:
For vista/7:
```
bootrec.exe /fixmbr
```

For XP:
```
fixmbr
```

---

### Post by YesWeCan on 2011-02-24
Here are some detailed instructions on how to do it:
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)


BTW, don't let your grub experience put you off linux. Unlike Windows, Ubuntu is not all made by the same group of people. It is, in fact, a collection of all sorts of software from different sources, most of which is high quality. IMO the grub application, although a major step forward compared to how it was a few years ago, is still pretty user-hostile and badly organised. Are you listening, Canonical? But the thing we love Ubuntu for is the kernel (which is much, much higher quality than Windows) and the graphical user interfaces, such as Gnome and KDE. With Microsoft, the GUI (the Windows interface) is inextricably tied to the underlying operating system (kernel). But in linux you can choose different Windows interfaces. Linux is pretty versatile and highly flexible. You need to learn how to tinker with it.

[edit]
Before I get flamed I had better add that none of this would be a problem if Microsoft would make their own boot loader standards compliant so that you could boot Ubuntu from it. :)

---

### Post by reallybadwithlinux on 2011-02-24
At this point I'd quote your posts to tell you who I'm referring to, but I'm writing this on my phone (bet you could guess why). Well I tried running the code you mentioned, and everything happened almost exactly  as you said, but after a reboot, nothing had changed. In the code (that I can't remember, or reference to), when you wrote 'sda', did you intend for me to replace that with MY drive? My Linux drive is sda5. 
Thanks again for taking an interest but so far there's been no luck. The DVD drive is also still a no go :(

I'm not against ubuntu or Linux in anyway, I've had it installed before. I usually take a look at it when I become overwhelmed with the boring windows look. I love the freedom in Linux, but unfortunately I could never see it replacing windows as I do a fair amount of video editing and there is select software that I need. But if I ever find myself with a spare computer, it's gonna be ubuntu all the way :).

---

### Post by Rubi1200 on 2011-02-24
I suggest you do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the _entire_ contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

Once we see the results it will be easier to figure out what is happening.

---

### Post by bcbc on 2011-02-24
> **reallybadwithlinux said:**
> At this point I'd quote your posts to tell you who I'm referring to, but I'm writing this on my phone (bet you could guess why). Well I tried running the code you mentioned, and everything happened almost exactly  as you said, but after a reboot, nothing had changed. In the code (that I can't remember, or reference to), when you wrote 'sda', did you intend for me to replace that with MY drive? My Linux drive is sda5. 
Thanks again for taking an interest but so far there's been no luck. The DVD drive is also still a no go :(

Next time run the command:
sudo fdisk -l (lower case -L)
and examine the partitions - make sure you note which drive is which. It's possible that your BIOS sees the USB as /dev/sda

If your internal drive is /dev/sdb then change as appropriate. But that's usually a guaranteed fix (unless there is some other reason windows won't boot)

**And don't try to install it to a partition.**

EDIT: just seen Rubi1200's post. Yes the bootinfoscript will tell us exactly what we need to fix it. You should be able to connect to the net from the live CD environment and post it instead of using your iPhone.

---

### Post by reallybadwithlinux on 2011-02-24
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Lilo is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /boot/bcd /Windows/System32/winload.exe 
                       /wubildr.mbr /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/BCD

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   266,242,922   266,242,860   7 HPFS/NTFS
/dev/sda2         366,073,155   390,716,864    24,643,710   7 HPFS/NTFS
/dev/sda3         266,244,094   366,071,807    99,827,714   5 Extended
/dev/sda5         266,244,096   361,897,983    95,653,888  83 Linux
/dev/sda6         361,900,032   366,071,807     4,171,776  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 3995 MB, 3995074560 bytes
80 heads, 16 sectors/track, 6096 cylinders, total 7802880 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          8,064     7,802,879     7,794,816   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        E0F8D9C0F8D994DE                       ntfs                                     
/dev/sda2        2C88743C8874071C                       ntfs       HP_RECOVERY                   
/dev/sda3: PTTYPE="dos" 
/dev/sda5        51e72558-fcf6-4f6d-a526-3882d517e1c1   ext4                                     
/dev/sda6        4e93d035-4229-43ff-a345-ab5c8b3ec28d   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        E62A-763C                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=51e72558-fcf6-4f6d-a526-3882d517e1c1 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=4e93d035-4229-43ff-a345-ab5c8b3ec28d none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 140.7GB: boot/grub/core.img
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  a2 d8 8d e4 40 9d 20 fa  41 98 33 ef 39 a8 7f dd  |....@. .A.3.9...|
00000010  21 9d 5e 90 8c c8 8b 45  09 42 50 04 50 78 56 de  |!.^....E.BP.PxV.|
00000020  6c f8 31 63 84 30 88 8c  c4 0c 49 48 29 12 2a 91  |l.1c.0....IH).*.|
00000030  aa 83 de 16 55 25 fb b0  4b 12 d5 72 40 38 5f 47  |....U%..K..r@8_G|
00000040  d9 25 d9 93 dc dd e9 ab  d2 46 c6 49 a8 52 ba 25  |.%.......F.I.R.%|
00000050  89 6a cb d5 89 62 48 41  56 5f 7f 54 d1 ea f6 64  |.j...bHAV_.T...d|
00000060  1e 66 28 9c 34 5c 0d b4  79 8a 3f b2 da 9d f0 bd  |.f(.4\..y.?.....|
00000070  54 57 e8 d7 b2 cf c5 ce  09 5f 53 e5 6a 87 5f 03  |TW......._S.j._.|
00000080  b2 cd 93 7b 05 a9 b8 50  fb d7 6e 45 2a 63 39 97  |...{...P..nE*c9.|
00000090  53 bc ba d1 24 4e 5d 07  ec c6 be 67 b1 77 0c c3  |S...$N]....g.w..|
000000a0  c5 6c ad d5 1f 4f 61 4b  ad b1 57 ad ea f6 41 5e  |.l...OaK..W...A^|
000000b0  58 c7 e1 04 03 6a e2 d2  65 ab 91 3d 30 80 30 3e  |X....j..e..=0.0>|
000000c0  12 ac 2f db b7 cd 0e ad  ec 23 12 95 c1 2e ab f4  |../......#......|
000000d0  2e a3 cf 66 fd 5f ed a8  bd 05 be 9e 8e 79 1d 01  |...f._.......y..|
000000e0  f4 7f a4 a9 e9 0b 64 b7  1f f7 a6 13 20 47 b1 ab  |......d..... G..|
000000f0  62 99 eb d5 5c 96 dd 57  77 37 de 66 4b 7f d3 96  |b...\..Ww7.fK...|
00000100  2b 63 5d 71 d3 21 32 60  a2 ad 55 96 e5 3f 48 3d  |+c]q.!2`..U..?H=|
00000110  0e 3c 0d a7 93 03 90 aa  3f 9e e0 09 fe 82 aa 6c  |.<......?......l|
00000120  6c b3 89 e1 d3 af d4 4e  c8 4e 07 e7 74 e9 64 dd  |l......N.N..t.d.|
00000130  62 ae 77 81 7c 71 46 95  59 4a c6 47 06 29 0b 79  |b.w.|qF.YJ.G.).y|
00000140  ea 20 65 7b 9d 16 f7 2b  e1 1c f3 db fa 2d 5b 3c  |. e{...+.....-[<|
00000150  33 59 9a 76 b8 32 ae 3c  be f7 a1 12 08 97 9f 0d  |3Y.v.2.<........|
00000160  d0 42 2a 64 18 62 e8 d9  d3 34 aa a8 64 66 14 eb  |.B*d.b...4..df..|
00000170  2c 01 3c 0e a5 b7 c7 bb  99 da 43 b8 e0 5e 2d 80  |,.<.......C..^-.|
00000180  78 25 f4 7b 40 b6 11 fb  5e fa db 91 04 9a e3 c1  |x%.{@...^.......|
00000190  98 63 6f 3e be fb 5b dd  37 2c 5a 24 eb 9d 5c bc  |.co>..[.7,Z$..\.|
000001a0  5b de fb 49 29 e1 89 b4  eb bf 81 1b 72 3b c8 7f  |[..I).......r;..|
000001b0  39 85 fd 20 02 3b e9 f9  eb b3 54 f2 74 f2 00 fe  |9.. .;....T.t...|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 90 b3 05 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 90  b3 05 00 b0 3f 00 00 00  |............?...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



```

---

### Post by bcbc on 2011-02-24
Ok lilo ended up on /dev/sdb (either you told it to go there, or the bios had the drive order switched??)

Anyway - rerun my original lilo instructions with /dev/sda.


Strangely, you still have your Ubuntu on /dev/sda5, but there is no grub.cfg. I suppose you could try and resurrect this later if you want.

---

### Post by Rubi1200 on 2011-02-24
I agree with bcbc; first get Windows back up and running and then we can reinstall GRUB if you want.

Other than that, I don't see any major issues with the results.

Let us know how things work out please or if you need more specific instructions.

---

### Post by reallybadwithlinux on 2011-02-24
SUCCESS!!! You guys are legends! I'm back in widnows! As for reinstalling GRUB, I think I'm gonna pass. My installation of ubuntu is broken anyway, so there's no point trying to boot in to it. I'd rather remove Ubuntu and reclaim the 40gb to my windows partition. Though, the last time I tried this I ended up ruining everything. Is it now safe to delete that partition? If not, how do I remove Ubuntu?
Once I reclaim this extra space, I may install with Wubi since I'm still very bored of Windows.

---

### Post by bcbc on 2011-02-24
> **reallybadwithlinux said:**
> SUCCESS!!! You guys are legends! I'm back in widnows! As for reinstalling GRUB, I think I'm gonna pass. My installation of ubuntu is broken anyway, so there's no point trying to boot in to it. I'd rather remove Ubuntu and reclaim the 40gb to my windows partition. Though, the last time I tried this I ended up ruining everything. Is it now safe to delete that partition? If not, how do I remove Ubuntu?
Once I reclaim this extra space, I may install with Wubi since I'm still very bored of Windows.

You just have to delete the logical partition that Ubuntu is on or reformat it. My computer (XP) shows it as "Healthy (Unknown)" and gives me the option to delete it. You can then recreate a new logical partition and format with ntfs in it's place.

If you use Wubi check this out [https://wiki.ubuntu.com/WubiGuide#Warning](https://wiki.ubuntu.com/WubiGuide#Warning) (and make sure you [uninstall]("https://wiki.ubuntu.com/WubiGuide#Uninstallation") the remnants you have as well)

---

### Post by YesWeCan on 2011-02-24
So where does Lilo live? The original problem was caused because Grub has a bunch of files it depends on in the Ubuntu partition. Is Lilo not dependent on this? Or is it that in this case Lilo just creates an MBR mimick of the Windows MBR?

---

### Post by bcbc on 2011-02-24
> **YesWeCan said:**
> So where does Lilo live? The original problem was caused because Grub has a bunch of files it depends on in the Ubuntu partition. Is Lilo not dependent on this? Or is it that in this case Lilo just creates an MBR mimick of the Windows MBR?
Extracted from man lilo:
> -M master-device [mbr|ext]
              Install  a Master Boot Record on the device specified as master-
              device, selecting the Standard or Extended  Master  Boot  Loader
              per the option.  The primary partition table on master-device is
              undisturbed.  If no valid Volume-ID (serial number) is  present,
              then generate one and write it to the MBR.  [B]If mbr is specified,
              the Standard Master Boot Loader will search partitions  1-4  for
              an active flag, and boot the flagged partition.  Only one active
              flag is allowed.[/B]  If ext is specified, the search for an  active
              partition  will  include extended partitions as well.  The pres-
              ence of the Extended Master  Boot  Loader  on  the  Master  Boot
              Record  (MBR  = sector 0) of a disk affects the operation of the
              -A option.

That's all the windows boot loader does... look for the partition marked active.

---

### Post by YesWeCan on 2011-02-24
That's a really simple method to fix the MBR for Windows. Thanks. :)

---

### Post by bcbc on 2011-02-24
> **YesWeCan said:**
> That's a really simple method to fix the MBR for Windows. Thanks. :)
I first saw it mentioned here on ubuntuforums.org and I've used it myself to good effect. So I am happy to pass it along! :) 

(Even though I have my windows DVDs I have never bothered to use them as lilo from Ubuntu is so much easier.)

---

### Post by Rubi1200 on 2011-02-25
> **reallybadwithlinux said:**
> SUCCESS!!! You guys are legends! I'm back in widnows! As for reinstalling GRUB, I think I'm gonna pass. My installation of ubuntu is broken anyway, so there's no point trying to boot in to it. I'd rather remove Ubuntu and reclaim the 40gb to my windows partition. Though, the last time I tried this I ended up ruining everything. Is it now safe to delete that partition? If not, how do I remove Ubuntu?
Once I reclaim this extra space, I may install with Wubi since I'm still very bored of Windows.
Excellent! Glad you got things sorted out in the end.

Follow bcbc's advice regarding the partitions and uninstalling Wubi correctly.

Good luck :)

---

### Post by reallybadwithlinux on 2011-02-25
Hey guys, I'm having some more trouble with Ubuntu. It isn't actually related to this post though, so would you prefer me to start a new thread? I just figured since this thread has already been solved and I've already used it to explain how new I am to Linux that it would be easier
My problem is Ubuntu booting into Busybox on startup. Do you think you guys could have a stab at it?

---

### Post by bcbc on 2011-02-25
What have you done since you fixed the last problem. Did you remove your old Ubuntu and reinstall Wubi?

---

### Post by reallybadwithlinux on 2011-02-25
Yeah, I completely removed the old ubuntu like you said. I was going to give Wubi a try, but I followed your link and read something about Wubi only being intended to demo the OS. I kinda agreed and just figured that I'd try another install on a different partition. 

Basically, the problem I'm having is the same as last time, though last time I thought the error must have come from having a bad install disc or something so I just tried to remove it (which is how everything went very wrong). But I'm having the problem again, and this time with a different disc.

Basically, when I boot Ubuntu from the GRUB menu, nothing loads. After around 20 seconds, a message appears on the screen saying 

"Gave up waiting for root device. Common Problems:
-boot args (cat /proc/ cmdline)
-check rootdelay= (did the system wait long enough?)
-Check root= (did the system wait for the right device?)
-Missing modules (cat /proc/modules: ls /dev)"

It then says "dropping to a shell" and brings up BusyBox v1.15.3 underneath.

I know that this message has told me all the possible faults, but I don't know how to fix them.

---

### Post by bcbc on 2011-02-25
> **reallybadwithlinux said:**
> Yeah, I completely removed the old ubuntu like you said. I was going to give Wubi a try, but I followed your link and read something about Wubi only being intended to demo the OS. I kinda agreed and just figured that I'd try another install on a different partition. 

Basically, the problem I'm having is the same as last time, though last time I thought the error must have come from having a bad install disc or something so I just tried to remove it (which is how everything went very wrong). But I'm having the problem again, and this time with a different disc.

Basically, when I boot Ubuntu from the GRUB menu, nothing loads. After around 20 seconds, a message appears on the screen saying 

"Gave up waiting for root device. Common Problems:
-boot args (cat /proc/ cmdline)
-check rootdelay= (did the system wait long enough?)
-Check root= (did the system wait for the right device?)
-Missing modules (cat /proc/modules: ls /dev)"

It then says "dropping to a shell" and brings up BusyBox v1.15.3 underneath.

I know that this message has told me all the possible faults, but I don't know how to fix them.
ok, why don't you run the bootinfoscript again so we can see what's up?

---

### Post by reallybadwithlinux on 2011-02-25
I suspect what is causing the problem should be present in the last bootinfo I posted, since I had this problem from the very beginning . Just in case though


```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /boot/bcd /Windows/System32/winload.exe 
                       /wubildr.mbr /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/BCD

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Windows Vista/7
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   287,255,693   287,255,631   7 HPFS/NTFS
/dev/sda2         366,073,155   390,716,864    24,643,710   7 HPFS/NTFS
/dev/sda3         287,256,574   366,071,807    78,815,234   5 Extended
/dev/sda5         287,256,576   362,745,855    75,489,280  83 Linux
/dev/sda6         362,747,904   366,071,807     3,323,904  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        E0F8D9C0F8D994DE                       ntfs                                     
/dev/sda2        2C88743C8874071C                       ntfs       HP_RECOVERY                   
/dev/sda3: PTTYPE="dos" 
/dev/sda5        eb22fccb-921d-40fd-9a7e-6cece7c3d933   ext4                                     
/dev/sda6        fb7b28d3-1db9-46b1-9171-bb3399a02339   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set eb22fccb-921d-40fd-9a7e-6cece7c3d933
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set eb22fccb-921d-40fd-9a7e-6cece7c3d933
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set eb22fccb-921d-40fd-9a7e-6cece7c3d933
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=eb22fccb-921d-40fd-9a7e-6cece7c3d933 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set eb22fccb-921d-40fd-9a7e-6cece7c3d933
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=eb22fccb-921d-40fd-9a7e-6cece7c3d933 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set eb22fccb-921d-40fd-9a7e-6cece7c3d933
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set eb22fccb-921d-40fd-9a7e-6cece7c3d933
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set e0f8d9c0f8d994de
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 2c88743c8874071c
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=eb22fccb-921d-40fd-9a7e-6cece7c3d933 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=fb7b28d3-1db9-46b1-9171-bb3399a02339 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 158.4GB: boot/grub/core.img
 160.3GB: boot/grub/grub.cfg
 147.9GB: boot/initrd.img-2.6.35-22-generic
 158.4GB: boot/vmlinuz-2.6.35-22-generic
 147.9GB: initrd.img
 158.4GB: vmlinuz

```

---

### Post by bcbc on 2011-02-25
> **reallybadwithlinux said:**
> I suspect what is causing the problem should be present in the last bootinfo I posted, since I had this problem from the very beginning . Just in case though

Your last bootinfo showed that the grub.cfg was missing. And that tells a large part of the story, so needed again.

But that all looks fine. So... no idea what the problem is! :(

---

### Post by reallybadwithlinux on 2011-02-25
No worries man :) I may post this as a new thread tomorrow. Thanks for taking a look.

---

