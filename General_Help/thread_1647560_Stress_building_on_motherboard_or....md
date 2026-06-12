---
title: "Stress building on motherboard or...?"
date: 2010-12-17
forum: General Help
---

### Post by anarchoskin69 on 2010-12-17
Hi guys, seems my Gateway DX4822 seems to have this problem every so often that can last a few days, week or even a month, then the problem vanishes suddenly. At first I thought it was stress building on the motherboard, which it may be, but I would like to seek all possible solutions to this. Originally, it only did this when I booted Windows 7, but since I dual-booted Ubuntu with GRUB it still does it, which is why i may think its not software related. Still, i visited the same sites with Ubuntu and recently gave a few apps in Ubuntu root access to shell so maybe it was a security breach, a "broken shell" now if you will. I booted a live CD and can still see files on hard drive, BIOS shows IDE detected on boot-up. anyways, i'll get to the problem and maybe you guys can share your weed of wisdom. and then maybe ill have less restless sleep. it is a refurbished model, so maybe it has something to do with that, being not all from the same hands of mold. so far this computer has been a love hate relationship, only because of this problem.

i boot the computer, and even when i entered BIOS and set it to do full BIOS tests everything came out fine, then in the middle of the boot after it finishes BIOS and the point where it should load software OS from hdd it shows "DVI" at top right of monitor and reboots, then repeats this process over and over again. i thought of back in the old days when you had to set hdd as master or slave, but remembered this was no longer necessary, so no "slaved chains" i guess. now its off and leaving ruptured silence. perhaps the GRUB bootloader was destroyed by the sometimes volatile sites i visit? the websites i visit are radical political websites shared on twitter, and sometimes links are quickly shared with viruses already in them to attack the radical political side I associate myself with or are sometimes compromised and uploaded to legitimate articles/websites/whatever.

basically, if its a motherboard issue i can take it into a local computer shop and get it replaced, but after booting the live CD and being able to see the drive i am positive thats not the problem. has the GRUB bootloader been compromised the same way the Windows bootloader was? but why does it work after a while, whether its 2 days, a week or a month? i was in the middle of finishing up a novel, plus i have tons of other important stuff on there. computer has been down a week or two now i think. any help is highly appreciated!

-anarchoskin69

---

### Post by anarchoskin69 on 2011-01-11
so its been a couple of weeks and i guess theres been no suggestions...?

---

### Post by anarchoskin69 on 2011-01-11
so I began lurking around here and found this Boot Info Script that I ran from my desktop, here are the contents of the results.txt file if anyone wants to take a look and offer any suggestions. I installed Windows 7 which was giving me this error on its own, then I installed Fedora and Ubuntu and this same problem of not booting is happening again.> **anarchoskin69 said:**
>                 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdg and looks on the same drive in 
    partition #7 for (,msdos7)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdg1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /BOOT/BCD

sdg2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sdg3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe

sdg4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdg5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst /grub/grub.conf

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 8032 MB, 8032092160 bytes
131 heads, 50 sectors/track, 2395 cylinders, total 15687680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               8,192    15,687,679    15,679,488   7 HPFS/NTFS


Drive: sdg ___________________ _____________________________________________________

Disk /dev/sdg: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdg1               2,048    31,459,327    31,457,280  27 Hidden HPFS/NTFS
/dev/sdg2    *     31,459,328    31,664,127       204,800   7 HPFS/NTFS
/dev/sdg3          31,664,128   895,848,279   864,184,152   7 HPFS/NTFS
/dev/sdg4         895,848,446 1,953,523,711 1,057,675,266   5 Extended
/dev/sdg5       1,695,760,384 1,696,784,383     1,024,000  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        0C24434324432ED0                       ntfs       PENDRIVE                      
/dev/sda: PTTYPE="dos" 
/dev/sdg1        A04CEAE64CEAB666                       ntfs       PQSERVICE                     
/dev/sdg2        4C06ED6C06ED580A                       ntfs       SYSTEM RESERVED               
/dev/sdg3        01CB64C445479D80                       ntfs       Gateway                       
/dev/sdg4: PTTYPE="dos" 
/dev/sdg5        406c0ea4-7f44-44fe-9ce0-b8e5f1f5a721   ext4                                     
/dev/sdg: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sda1        /cdrom                   fuseblk    (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sdg3/boot.ini: ================================

[boot loader] 
default=2323 
[operating systems] 
2323=/bootlogo /noguiboot /bootlogo /noguiboot 

============================= sdg5/grub/grub.conf: =============================

# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /boot/, eg.
#          root (hd0,4)
#          kernel /vmlinuz-version ro root=/dev/mapper/VolGroup-lv_root
#          initrd /initrd-[generic-]version.img
#boot=/dev/sda
default=0
timeout=5
splashimage=(hd0,4)/grub/splash.xpm.gz
hiddenmenu
title Fedora (2.6.34.7-56.fc13.i686)
    root (hd0,4)
    kernel /vmlinuz-2.6.34.7-56.fc13.i686 ro root=/dev/mapper/VolGroup-lv_root rd_LVM_LV=VolGroup/lv_root rd_LVM_LV=VolGroup/lv_swap rd_NO_LUKS rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=us rhgb quiet
    initrd /initramfs-2.6.34.7-56.fc13.i686.img
title Fedora (2.6.33.3-85.fc13.i686)
    root (hd0,4)
    kernel /vmlinuz-2.6.33.3-85.fc13.i686 ro root=/dev/mapper/VolGroup-lv_root rd_LVM_LV=VolGroup/lv_root rd_LVM_LV=VolGroup/lv_swap rd_NO_LUKS rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=us rhgb quiet
    initrd /initramfs-2.6.33.3-85.fc13.i686.img
title Other
    rootnoverify (hd0,1)
    chainloader +1

=================== sdg5: Location of files loaded by Grub: ===================


 868.5GB: grub/grub.conf
 868.5GB: grub/menu.lst
 868.5GB: grub/stage2
 868.2GB: initramfs-2.6.33.3-85.fc13.i686.img
 868.2GB: initramfs-2.6.34.7-56.fc13.i686.img
 868.2GB: vmlinuz-2.6.33.3-85.fc13.i686
 868.2GB: vmlinuz-2.6.34.7-56.fc13.i686
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde sdf 

---

### Post by mastablasta on 2011-01-11
are there any other error messages? did you do a check disk?
 
You can check the motherboard if any capacitors are bulged.
 
why you don't need to set master and slave disk? have you tried setting it anyway?

---

### Post by Mark Phelps on 2011-01-11
Doesn't sound like the typical motherboard problems -- especially if you can run find from CD without problems.

If I had to guess (and I do at this point), I would suspect either the power supply or hard drive, or both.

I mention the power supply because I had my second Antec PSU burn out this last weekend, and this time, it took the motherboard with it!  Was experiencing all kind of boot failures just prior to this.  

And, when the motherboard went, the video went first.

So, since it looks like you're rebooting when trying to bring up the video, it could be the PSU.

---

### Post by cascade9 on 2011-01-11
I'd tend to agree with Mark Phelps ;) 

Sounds more like a power supply or hard drive issue. It could be video card as well (I'd guess that 'dvi' is the monitor trying to sync with the video card, but failing) or the motherboard, but power supply is my guess. 

sorry its only a guess, but sometimes these intermittent faults are very hard to track down, even with the computer in front of you. A great example is a computer a friend of mine had me fix- once every couple of boots, it would shutdown after 3-5 seconds. They had replaced power supply, motherboard and CPU, then they brought it to me to test the RAM. Guess what it was? A sitcky power button :S

---

