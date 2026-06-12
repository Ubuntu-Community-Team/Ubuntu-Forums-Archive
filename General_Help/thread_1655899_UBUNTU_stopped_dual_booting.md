---
title: "UBUNTU stopped dual booting"
date: 2010-12-30
forum: General Help
---

### Post by Berry Greene on 2010-12-30
Oh my word am I making hard work of the Forum. please forgive.

I have been operating a dual boot system of Ubuntu (8.04.1 when installed but many updates?) - together with Windows XP for over one year. Fantastic - just need Windows now for the odd program (Pinnacle). 
All worked fine until recently when UBUNTU no longer boots up. I do get some sort of cursor entry and the word GRUB appears, together with a menu.

But what shall I enter there - if anything?  No selections make sense to me.

Partitioned disk - all checks seem OK. Windows still boots & runs OK. Files still in UBUNTU partition. Live disc operates OK.
Cannot recall  how to re-install UBUNTU to keep dual boot mode. 

Please prompt me and apologies if I am not operating the Forum (or anything else) in the right way. I cannot surely be this thick. Really!

Sincerely, Berry Greene:guitar:

---

### Post by Quackers on 2010-12-30
Did you install via wubi?
Did an update cause this problem?
Does Windows just boot up directly, or through a menu selection?

---

### Post by Berry Greene on 2010-12-30
> **Quackers said:**
> Did you install via wubi?
Did an update cause this problem?
Does Windows just boot up directly, or through a menu selection?

Hi.

I cannot recall this "wubi" that you mention. My mind is blank on exactly what the procedure for installation was. Even my notes don't seem to record anything.

I don't think an update caused the problem BUT - it could have been that as I have been in the habit of actioning updates. Is that a bad policy then?

Windows boots through a menu selection. You get 10 secs to alter it to UBUNTU - after which it defaults to Windows XP. (You can also hasten Windows by pressing enter).

BG

---

### Post by Quackers on 2010-12-30
So it seems that you are getting to the grub menu, with Windows the highlighted option and Ubuntu underneath. Yes?
If you choose Windows it boots but Ubuntu just goes to a grub prompt?
If this is correct please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by bcbc on 2010-12-30
It sounds like it could be a wubi install by your description (windows boot manager first?).

Why don't you run the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") and post the results so we can see what's going on...

EDIT: snap!

---

### Post by Quackers on 2010-12-30
:-) when unsure run the boot script :-)

---

### Post by Berry Greene on 2010-12-30
> **Quackers said:**
> So it seems that you are getting to the grub menu, with Windows the highlighted option and Ubuntu underneath. Yes?
If you choose Windows it boots but Ubuntu just goes to a grub prompt?
If this is correct please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Righto Quackers & bcbc. Thanks for that. It will be done now but could take a little while.

---

### Post by Berry Greene on 2010-12-30
> **Quackers said:**
> So it seems that you are getting to the grub menu, with Windows the highlighted option and Ubuntu underneath. Yes?
If you choose Windows it boots but Ubuntu just goes to a grub prompt?
If this is correct please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Hello Quackers 102 96948
Oh boy! Trouble getting internet to run then - you don't wanna know! Got it done now. Should I be able to "attach" it? Tried it...  but can't seem to....  but anyway....... 

There are actually 3 HDDs - 
One with 3 partitions. One of these is for UBUNTU, - One for Windows, - and one for data. (1TB drive)
A Second HDD used for data (400Gb drive) ... and
A third "physical?" HDD (200Mb) that had original version of Windows on it but now used for data only.  {Orig Windows but crashed. Kept for data but fragments will still be there}. 
Thank you for your forbearance.
Here is the file :-
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr /wubildr

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/menu.lst /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x37d78709

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   430,060,049   430,059,987   7 HPFS/NTFS
/dev/sda2         430,076,115   532,490,489   102,414,375   7 HPFS/NTFS
/dev/sda3         532,490,490 1,953,520,064 1,421,029,575   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x59218501

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   390,716,864   390,716,802   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xbabdc283

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   781,417,664   781,417,602   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        98F4294BF4292D46                       ntfs       First Part of HDD1- XP-System 
/dev/sda2        BACC2D4BCC2D036D                       ntfs       Second Part of HDD1-UBUNTU-Systm
/dev/sda3        550CF6A5027BC8A7                       ntfs       Third Part of HDD1-B-Up Data  
/dev/sdb1        1C0C61B10C61871C                       ntfs       Original System&Data HDD      
/dev/sdc1        6604E21704E1EA4F                       ntfs       Data Only HDD                 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /media/First Part of HDD1- XP-System fuseblk    (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/sda2        /media/Second Part of HDD1-UBUNTU-Systm fuseblk    (rw,nosuid,nodev,noatime,allow_other,blksize=4096)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=15 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptOut 
c:\wubildr.mbr="Ubuntu" 

======================== sda2/ubuntu/winboot/menu.lst: ========================

debug off
hiddenmenu
default 0
timeout 0
fallback 1

title find /ubuntu/disks/boot/grub/menu.lst
    find --set-root --ignore-floppies /ubuntu/disks/boot/grub/menu.lst
    configfile /ubuntu/disks/boot/grub/menu.lst

title find /ubuntu/install/boot/grub/menu.lst
    fallback 2
    find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst
    configfile /ubuntu/install/boot/grub/menu.lst

title find /menu.lst
    fallback 3
    find --set-root --ignore-floppies /menu.lst
    configfile /menu.lst

title find /boot/grub/menu.lst
    fallback 4
    find --set-root --ignore-floppies /boot/grub/menu.lst
    configfile /boot/grub/menu.lst

title find /grub/menu.lst
    fallback 5
    find --set-root --ignore-floppies /grub/menu.lst
    configfile /grub/menu.lst

title commandline
    commandline

title reboot
    reboot

title halt
    halt

================================ sdb1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn 
=======Devices which don't seem to have a corresponding hard drive==============

sdd sde sdf sdg sdh

---

### Post by Berry Greene on 2010-12-30
I really am at sea with the operation of this Forum - and much else it would seem! Sorry can't help it. NEway the information you need ought to be here now but also see older posts please. Berry G



```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr /wubildr

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/menu.lst /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x37d78709

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   430,060,049   430,059,987   7 HPFS/NTFS
/dev/sda2         430,076,115   532,490,489   102,414,375   7 HPFS/NTFS
/dev/sda3         532,490,490 1,953,520,064 1,421,029,575   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x59218501

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   390,716,864   390,716,802   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xbabdc283

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   781,417,664   781,417,602   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        98F4294BF4292D46                       ntfs       First Part of HDD1- XP-System 
/dev/sda2        BACC2D4BCC2D036D                       ntfs       Second Part of HDD1-UBUNTU-Systm
/dev/sda3        550CF6A5027BC8A7                       ntfs       Third Part of HDD1-B-Up Data  
/dev/sdb1        1C0C61B10C61871C                       ntfs       Original System&Data HDD      
/dev/sdc1        6604E21704E1EA4F                       ntfs       Data Only HDD                 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /media/First Part of HDD1- XP-System fuseblk    (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/sda2        /media/Second Part of HDD1-UBUNTU-Systm fuseblk    (rw,nosuid,nodev,noatime,allow_other,blksize=4096)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=15 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptOut 
c:\wubildr.mbr="Ubuntu" 

======================== sda2/ubuntu/winboot/menu.lst: ========================

debug off
hiddenmenu
default 0
timeout 0
fallback 1

title find /ubuntu/disks/boot/grub/menu.lst
    find --set-root --ignore-floppies /ubuntu/disks/boot/grub/menu.lst
    configfile /ubuntu/disks/boot/grub/menu.lst

title find /ubuntu/install/boot/grub/menu.lst
    fallback 2
    find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst
    configfile /ubuntu/install/boot/grub/menu.lst

title find /menu.lst
    fallback 3
    find --set-root --ignore-floppies /menu.lst
    configfile /menu.lst

title find /boot/grub/menu.lst
    fallback 4
    find --set-root --ignore-floppies /boot/grub/menu.lst
    configfile /boot/grub/menu.lst

title find /grub/menu.lst
    fallback 5
    find --set-root --ignore-floppies /grub/menu.lst
    configfile /grub/menu.lst

title commandline
    commandline

title reboot
    reboot

title halt
    halt

================================ sdb1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn 
=======Devices which don't seem to have a corresponding hard drive==============

sdd sde sdf sdg sdh   
```

---

### Post by bcbc on 2010-12-30
OK so you have a wubi install. But the virtual disks are missing. You are supposed to have an \ubuntu\disks folder (probably on D:[SIZE="1"] [/SIZE]?) containing the root.disk and swap.disk and a boot folder within that containing kernels and the grub menu (this is standard on wubi installed on older versions with grub legacy). But it appears that the entire \ubuntu\disks directory is missing or empty? Can you check this?

The [wubi guide]("https://wiki.ubuntu.com/WubiGuide") mentions:> Note that sometimes files are moved by Windows into a hidden folder called c:\found.000. You need to have c:\ubuntu\disks\root.disk and c:\ubuntu\disks\boot. If you do not see those, look for found.000. You need to change the Windows Explorer settings to be able to see hidden folders first, then move the files from found.000 to their original location.
You might want to look on d: or whatever drive you installed wubi on as well.

---

### Post by Berry Greene on 2010-12-31
Hello BCBC 10296948           12:25 (UK GMT) 31Dec2010
Thank you for your reply. Time differenced delays my response. (I think!). Are you in US?
I will expand on the info. that I sent last time. I am getting better with operating the Forum - I hope! In the following please allow for my getting "Physical" & "Logical" terms around the wrong way!

There are actually 3 (PHYSICAL?) HDDs in my PC - and as the big one is partitioned into 3 that makes 6 (LOGICAL?) disks identified as:-
C: (200Gb for WINDOWS XP PRO) - 
J:\ (50Gb for UBUNTU)
K:\ (700Gb for data)
D:\ (400Gb for data)
M:\ (200Gb now used for data) This was original WINDOWS XP HOME which failed and led me to use UBUNTU

Now I have looked for the things that you asked of me. I use a program called XTREE because (which runs under Windows - then called ZTREE) because I am more familiar with it and can see hidden files and do sorts & searches.
This is what it reports:-

In the root of HDD J:\ the UBUNTU partition of the first 1Tb disk- it reports folder & files:-
Found.000/dir000.chk/boot/grub with files inside both BOOT & GRUB
                               /shared/ No files here

These I think are the files that you are asking me to move. However, I'm not sure where to. They are on the UBUNTU partition but are they in the right folder?
There are other UBUNTU folders present.

Now also in the root of C:\ (The WINDOWS XP PRO installation which is part of the dual boot and works OK) I can see a couple of files called wubilder (no suffix) and wubilder.mbr

I cannot find any other familiar files anywhere. Only C:\ & J:\ have active boot in the root (although M:\ does have the now defunct WINDOWS XP HOME boot stuff. This isn't set to be looked at in the BIOS anyway. When it went wrong I got a new bigger drive (now partitioned as C:\ - J:\ & K:\   on which to re-install WINDOWS & UBUNTU.

To conclude yes I think you're quite right that WINDOWS has moved these files. Please just confirm that & where I am to move them.

Thank you for your forbearance, and I wish you a HAPPY NEW YEAR!
Berry.

---

### Post by bcbc on 2010-12-31
Canada (West Coast) - so there's a little difference ;)

OK so wubildr and wubildr.mbr on c:\ is normal. Wubi boots from the Windows boot manager so it's normal to have these on the main windows partition (even windows recovery partitions get them).

_For wubi with grub legacy - prior to release 9.10 (*note for others*)_
You need to have:
J:\ubuntu\disks\root.disk
J:\ubuntu\disks\swap.disk
(there may be other such as home.disk or usr.disk, usually just root.disk and swap.disk if you install on ntfs, and didn't create them yourself)

J:\ubuntu\disks\boot folder that contains
J:\ubuntu\disks\boot\abi-xxxxx
J:\ubuntu\disks\boot\config-xxxxx
J:\ubuntu\disks\boot\initrd.img-xxxxx
J:\ubuntu\disks\boot\System.map-xxxxx
J:\ubuntu\disks\boot\vmcoreinfo-xxxxx
J:\ubuntu\disks\boot\vmlinuz-xxxxx

J:\ubuntu\disks\boot\grub folder that contains
J:\ubuntu\disks\boot\grub\default
J:\ubuntu\disks\boot\grub\device.map
J:\ubuntu\disks\boot\grub\grubenv
J:\ubuntu\disks\boot\grub\menu.lst

If you can get all those you should be good to go. All your actual Ubuntu data/apps/settings are on the root.disk. That's the important one if it becomes a recovery mission.

Hopefully you have all that - good luck and Happy New Year to you too.

---

### Post by Quackers on 2010-12-31
Sorry about my lack of response Berry Greene, but when I see the word wubi my eyes glaze over :-) I know less about wubi than I know about nuclear physics - and I don't know too much about that :wink:
Fortunately bcbc (whom I now suspect is named after a place) is around! He knows ALL about wubi :-)  which makes me happy :-) (see)  If bcbc can't sort you out, your system is beyond help :wink:

---

### Post by Berry Greene on 2010-12-31
OK chaps!  Thanks to bcbc as you so rightly say, I am now "speaking" to you from UBUNTU again.

I just moved everything inside those folders and reconstructed the tree as you described.
Now it has rebooted and no data or set up seems to have been lost. Thanks so much.

Just to note that files GRUBENV and VMCOREINFO.XXXX did not exist so I  just went for it without them. Last question I promise. Can I - should I - remove the  now empty found.000 part of the tree from J:\

Fantastic but a bit of a workout for me these days. I'm not much at nuclear stuff either; in fact embarrassed to say that I don't seem too good at anything these days! However, and this is absolutely true - I have just repaired our toaster! That's much harder than nuclear physics and dual boot UBUNTU put together! FACT! Want hot toast? You got it. Want burnt toast - You got that too!

Regards & thanks. Berry Greene[IMG]http://ubuntuforums.org/images/icons/icon7.gif[/IMG]

---

### Post by Quackers on 2010-12-31
Any fish? :-)

---

### Post by Berry Greene on 2010-12-31
Solved OK now. How do I mark that?:guitar:

---

### Post by bcbc on 2011-01-01
> **Berry Greene said:**
> OK chaps!  Thanks to bcbc as you so rightly say, I am now "speaking" to you from UBUNTU again.

I just moved everything inside those folders and reconstructed the tree as you described.
Now it has rebooted and no data or set up seems to have been lost. Thanks so much.

Just to note that files GRUBENV and VMCOREINFO.XXXX did not exist so I  just went for it without them. Last question I promise. Can I - should I - remove the  now empty found.000 part of the tree from J:\

Fantastic but a bit of a workout for me these days. I'm not much at nuclear stuff either; in fact embarrassed to say that I don't seem too good at anything these days! However, and this is absolutely true - I have just repaired our toaster! That's much harder than nuclear physics and dual boot UBUNTU put together! FACT! Want hot toast? You got it. Want burnt toast - You got that too!

Regards & thanks. Berry Greene[IMG]http://ubuntuforums.org/images/icons/icon7.gif[/IMG]
Glad to hear it's sorted!

Keep backups for the future - just in case...

PS click on thread tools, mark as solved

---

