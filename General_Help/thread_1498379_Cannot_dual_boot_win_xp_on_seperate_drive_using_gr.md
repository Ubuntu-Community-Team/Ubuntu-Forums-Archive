---
title: "Cannot dual boot win xp on seperate drive using grub2, mythbuntu 10.04 lucid lynx"
date: 2010-05-31
forum: General Help
---

### Post by bitburger on 2010-05-31
Hi

I have issues with my dual boot setup. I cannot boot windows xp from grub2 that was installed with mythbuntu 10.04.
Windows and ubuntu is on two different hard drives.

History:
First I only had windows installed.
I put in an new hard drive and configured BIOS to boot from the new drive.
I installed mythbuntu 10.04 lucid lynx to the new drive 
In the last setup step I went in to advanced settings and chose to install the bootloader (grub) on the same drive as mythbuntu.
Everything went fine and ubuntu works great.

I now wanted to boot back in to windows and chose the windows entry in the grub menu.
I get a black screen with the message:
A disk read error occurred
Press Ctrl+Alt+Delete

I can still boot windows if I change BIOS boot order so that the windows drive is first, but I cannot boot windows from the grub menu.

Below is parts of my RESULT.txt as produced by the boot info script.

Thanks in advance


```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
 => Grub 2 is installed in the MBR of /dev/sdd and looks on the same drive in 
    partition #1 for /boot/grub.
 => No known boot loader is installed in the MBR of /dev/sde
 => Windows is installed in the MBR of /dev/sdf

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       xfs
    Boot sector type:  -
    Boot sector info:  
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

sdd1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdd2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdd5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sde1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdf1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 10.0 GB, 10005037056 bytes
255 heads, 63 sectors/track, 1216 cylinders, total 19541088 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    15,888,284    15,888,222  83 Linux
/dev/sda2          15,888,285    19,535,039     3,646,755   5 Extended
/dev/sda5          15,888,348    16,450,559       562,212  82 Linux swap / Solaris
/dev/sda6          16,450,623    19,535,039     3,084,417  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   488,392,064   488,392,002   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63 1,953,520,064 1,953,520,002   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *          2,048   224,827,391   224,825,344  83 Linux
/dev/sdd2         224,829,438   234,440,703     9,611,266   5 Extended
/dev/sdd5         224,829,440   234,440,703     9,611,264  82 Linux swap / Solaris


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sde1                  63   488,392,064   488,392,002   7 HPFS/NTFS


Drive: sdf ___________________ _____________________________________________________

Disk /dev/sdf: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdf1                  63   488,392,064   488,392,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        00e12e66-337b-4cfa-aa35-3a4b8371db19   ext3                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        5160fe4b-a09a-475a-8af0-a3fee887362a   swap                                     
/dev/sda6        195e5e57-68b2-4f52-b57a-5e09b5f36c71   xfs                                      
/dev/sda: PTTYPE="dos" 
/dev/sdb1        B4E065B8E065820A                       ntfs                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        886896FB6896E76A                       ntfs       Storage                       
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        9ca9e059-703b-47f4-8ca0-a19811ef65a1   ext4                                     
/dev/sdd2: PTTYPE="dos" 
/dev/sdd5        0f71dbcc-f3b5-483a-91de-cacd122c767c   swap                                     
/dev/sdd: PTTYPE="dos" 
/dev/sde1        66CC327ACC324519                       ntfs       Storage                       
/dev/sde: PTTYPE="dos" 
/dev/sdf1        A4704AEB704AC3B0                       ntfs       MY PASSPORT                   
/dev/sdf: PTTYPE="dos" 

================================ sdb1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn 

=========================== sdd1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd3,1)'
search --no-floppy --fs-uuid --set 9ca9e059-703b-47f4-8ca0-a19811ef65a1
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd3,1)'
search --no-floppy --fs-uuid --set 9ca9e059-703b-47f4-8ca0-a19811ef65a1
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd3,1)'
    search --no-floppy --fs-uuid --set 9ca9e059-703b-47f4-8ca0-a19811ef65a1
    linux    /boot/vmlinuz-2.6.32-22-generic-pae root=UUID=9ca9e059-703b-47f4-8ca0-a19811ef65a1 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd3,1)'
    search --no-floppy --fs-uuid --set 9ca9e059-703b-47f4-8ca0-a19811ef65a1
    echo    'Loading Linux 2.6.32-22-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-22-generic-pae root=UUID=9ca9e059-703b-47f4-8ca0-a19811ef65a1 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd3,1)'
    search --no-floppy --fs-uuid --set 9ca9e059-703b-47f4-8ca0-a19811ef65a1
    linux    /boot/vmlinuz-2.6.32-21-generic-pae root=UUID=9ca9e059-703b-47f4-8ca0-a19811ef65a1 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd3,1)'
    search --no-floppy --fs-uuid --set 9ca9e059-703b-47f4-8ca0-a19811ef65a1
    echo    'Loading Linux 2.6.32-21-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-21-generic-pae root=UUID=9ca9e059-703b-47f4-8ca0-a19811ef65a1 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd3,1)'
    search --no-floppy --fs-uuid --set 9ca9e059-703b-47f4-8ca0-a19811ef65a1
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd3,1)'
    search --no-floppy --fs-uuid --set 9ca9e059-703b-47f4-8ca0-a19811ef65a1
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu 9.10, kernel 2.6.31-14-generic (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 00e12e66-337b-4cfa-aa35-3a4b8371db19
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=00e12e66-337b-4cfa-aa35-3a4b8371db19 ro quiet
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode) (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 00e12e66-337b-4cfa-aa35-3a4b8371db19
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=00e12e66-337b-4cfa-aa35-3a4b8371db19 ro single
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.28-16-generic (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 00e12e66-337b-4cfa-aa35-3a4b8371db19
    linux /boot/vmlinuz-2.6.28-16-generic root=UUID=00e12e66-337b-4cfa-aa35-3a4b8371db19 ro quiet splash
    initrd /boot/initrd.img-2.6.28-16-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.28-16-generic (recovery mode) (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 00e12e66-337b-4cfa-aa35-3a4b8371db19
    linux /boot/vmlinuz-2.6.28-16-generic root=UUID=00e12e66-337b-4cfa-aa35-3a4b8371db19 ro single
    initrd /boot/initrd.img-2.6.28-16-generic
}
menuentry "Ubuntu 9.10, memtest86+ (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 00e12e66-337b-4cfa-aa35-3a4b8371db19
    linux /boot/memtest86+.bin 
}
menuentry "Microsoft Windows XP Professional (on /dev/sdb1)" {
    insmod ntfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set b4e065b8e065820a
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "My Win XP (on /dev/sdb1)" {
        insmod ntfs
        set root='(hd1)'
        search --no-floppy --fs-uuid --set b4e065b8e065820a
        chainloader +1
}

### END /etc/grub.d/40_custom ###


=================== sdd1: Location of files loaded by Grub: ===================


  21.6GB: boot/grub/core.img
  13.2GB: boot/grub/grub.cfg
  21.7GB: boot/initrd.img-2.6.32-21-generic-pae
  21.7GB: boot/initrd.img-2.6.32-22-generic-pae
  21.6GB: boot/vmlinuz-2.6.32-21-generic-pae
  21.7GB: boot/vmlinuz-2.6.32-22-generic-pae
  21.7GB: initrd.img
  21.7GB: initrd.img.old
  21.7GB: vmlinuz
  21.6GB: vmlinuz.old

```

---

### Post by harrismh777 on 2010-05-31
Well, based on your grub menu.lst info I think you chainloader is pointed at the wrong disk. 
If windows is installed on the first drive first partition (sda1) then the root for windows is hd0,0.   
Your grub info for xp is showing windows on sdb1 ??  with set root = hd1... this is probably not what you want.
Assuming windows xp is on sda1 (first drive, first partition) then set root has to be hd0     (hd0,0)
The partitions are numbered from 1 in fdisk sda1 (first drive, first partition).
The partitions are numbered from 0 in grub hd0,0  (first drive, first partition).
Grub chainloader needs to know how to find windows on the first drive, first partition, and cannot because the menu.lst is wrong...

I think so...   

The cool thing about grub is that you can give it commands at bootup... without changing the config... to see if it works. Try telling it where the xp partition is from the bootup menu and see if you can get it to work.

---

### Post by bitburger on 2010-05-31
Thanks for your reply

Actually Windows is installed on sdb.

sda has an old installation of ubuntu 9.10 on it which I dont use anymore. I should probably just remove that drive i guess.

With windows on sdb does the menu entry for windows look alright?

---

### Post by harrismh777 on 2010-05-31
> **bitburger said:**
> Thanks for your reply
[snip]

With windows on sdb does the menu entry for windows look alright?

Actually, no I don't think so. 

sdb1 is second disk, first partition.  

set root should be   set root = (hd1,0)   [ I think ]

Yours says,  (hd1)

If windows is on the second drive, first partition, trying  using 
set root = (hd1,0)  and see if that works.

---

### Post by bitburger on 2010-05-31
I did some more testing

The below is the entry from the grub os prober. This does NOT work
```

menuentry "Microsoft Windows XP Professional (on /dev/sdb1)" {
        insmod ntfs
        set root='(hd1,1)'
        search --no-floppy --fs-uuid --set b4e065b8e065820a
        drivemap -s (hd0) ${root}
        chainloader +1
}

```I have then tried the below as my custom entries and they do NOT work either.

```

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "My Win XP (on /dev/sdb1)" {
        insmod ntfs
        set root='(hd1,0)'
        search --no-floppy --fs-uuid --set b4e065b8e065820a
        drivemap -s (hd0) ${root}
        chainloader +1
}

menuentry "My Win XP test witout drivemap (on /dev/sdb1)" {
        insmod ntfs
        set root='(hd1,0)'
        search --no-floppy --fs-uuid --set b4e065b8e065820a
        chainloader +1
}
### END /etc/grub.d/40_custom ###

```As you mentioned I would also think it should be (hd1,0)
I don't remember now why I tried one option witout the drivemap. I read it somewhere. The other entry I had with only (hd1) was also something I read somewhere else that I tried.

What should the drivemap line be?

---

### Post by harrismh777 on 2010-05-31
I have never used the drivemap line... ??  you got me there.

Try this:

title           Microsoft Windows XP
rootnoverify    (hd1,0)
savedefault
makeactive
chainloader     +1

---

### Post by wilee-nilee on 2010-05-31
You have grub legacy in sda and grub2 in the mythbuntu sdd. I would wait for some qualified help here and those of you that want to throw answers may want to back off as we are talking about somebodies OS that if messed with in a incorrect manner may be lost for good.
Remove the sda drive and run the bootscript again.

---

### Post by harrismh777 on 2010-05-31
> **wilee-nilee said:**
> I would wait for some qualified help here and those of you that want to throw answers may want to back off as we are talking about somebodies OS that if messed with in a incorrect manner may be lost for good.
Remove the sda drive and run the bootscript again.

ouch...

#-o

(what was I thinking?)

---

### Post by wilee-nilee on 2010-05-31
> **harrismh777 said:**
> ouch...

#-o

(what was I thinking?)

If your going to quote me you left out the important part grub-legacy and grub2, carry on.

---

### Post by harrismh777 on 2010-05-31
> **wilee-nilee said:**
> If your going to quote me you left out the important part grub-legacy and grub2, carry on.


yup... searching grub2 on the forums shows multiple issues.

... just one more reason to stay with jaunty for a while. grub2 is not ready for prime time, looks like... several folks unable to boot into xp after updating to 9.1 or 10.04 (say grub2) and particularly if xp is on a diff drive.  not good.

[sigh]

:confused:

---

### Post by wilee-nilee on 2010-06-01
> **harrismh777 said:**
> yup... searching grub2 on the forums shows multiple issues.

... just one more reason to stay with jaunty for a while. grub2 is not ready for prime time, looks like... several folks unable to boot into xp after updating to 9.1 or 10.04 (say grub2) and particularly if xp is on a diff drive.  not good.

[sigh]

:confused:

I wouldn't use the forum as a indicator on grub2 personally I like it much better then grub-legacy, but I never got the hang of loading in missing boot stuff. I just install knowing where stuff is supposed to go such as grub, and since I multi-boot I know how to load the various systems bootloaders in case needed.

This is actually a free bump.

---

### Post by bitburger on 2010-06-01
Hi
i am away from the computer right now but i will try with removing sda with 9.10.
I`ll let you know what happens.

Thanks again for all the help

---

### Post by bitburger on 2010-06-07
I have not tried to remove sda yet. I would like to have this working with all the current drives in.

Does anyone know what might be wrong?

Thanks

---

### Post by bitburger on 2010-06-07
After reading about dual boot on two hard drives on [http://members.iinet.net.au/~herman546/p24.html]("http://members.iinet.net.au/%7Eherman546/p24.html") I think there is more information I can give on my setup.
I belive I did the same thing as in the above link. My drive setup is different however.

This is my situation.

According to BIOS 
Primary Master is a 10G IDE drive (sda with ubuntu 9.10)
Primary Slave is the DVD drive
Secondary Master is "Not detected"
Secondary Slave is "Not detected"
Third Master is a 250GB SATA on the motherboard (sdb with Win XP)
Fourth Master is a 1TB SATA on the motherboard (sdc used for data storage)

Then I have a PCI card with two extra SATA connections:
The first is 120GB (sdd with mythbuntu 10.04, this is the one I have setup BIOS to boot from)
The second is 250GB (sde used for data storage)

Then I also have a 250 GB external USB drive (sdf used for data backups)

In the BIOS I can see all drives and I can choose to boot from sdd which will bring up the GRUB 2 menu and then boot mythbuntu 10.04. Or I can tell BIOS to boot sdb which will boot Win XP.
I can NOT however boot win XP from GRUB 2 when sdd is set up as the first boot drive in BIOS

Let me know if there is any more info that I can give that will help solve this.

Thanks.

---

### Post by darkod on 2010-06-07
OK, lets try this:

1. Disconnect the usb hdd for now.

2. Go into BIOS and make sure sdd (10.04 disk) is first in hdd boot order. You don't have to do this if you are already sure. :)

Boot 10.04 and create new device.map to make sure the hdX mapping is right:

sudo grub-mkdevicemap

Update the grub.cfg:

sudo update-grub

Restart, keep 10.04 as first boot disk, try the 10.04 entry from grub2 and the XP entry. Let us know how it went.

---

### Post by bitburger on 2010-06-08
Thanks for your help.

I tried what you suggested but still cannot boot Win XP. Booting mythbuntu works.

where can I find device.map to see if it looks ok?

---

### Post by kansasnoob on 2010-06-08
The first thing I notice is that you said,

> Below is **[COLOR="Red"]parts[/COLOR]** of my RESULT.txt as produced by the boot info script.

It's also been a week so I'd really like to have you run the Boot Info Script again and attach the full output. Even though you're not using the sda menu.lst it may provide some clues, but I'd really like to see **the full output**.

Sometimes some seemingly insignificant thing is just what's needed, but that said I have one thought. Basically the Windows entry in grub 2 is:

> menuentry "Microsoft Windows XP Professional (on /dev/sdb1)" {
    insmod ntfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set b4e065b8e065820a
    **[COLOR="Red"]drivemap -s (hd0) ${root}[/COLOR]**
    chainloader +1
}

Where the drivemap -s uses (hd0), well that sort of makes my head spin. Both grub 2 and legacy grub begin counting drives with zero so (hd0) is the drive with a legacy grub mbr.

As easy as it is to restore an mbr I'd try booting into Lucid on sdd1 and installing it's grub to the mbr of both sda and sdd like:

```
sudo grub-install /dev/sda
```

```
sudo grub-install /dev/sdd
```

If either of the above return any errors also run:

```
sudo grub-install --recheck /dev/sdX
```

Of course you must replace the X with the proper drive designation. And always run "sudo update-grub" after making any changes.

---

### Post by kansasnoob on 2010-06-08
> **king john said:**
> Try right clicking on My Computer on the start menu  from xp. Choose Properties, and click the Advanced Tab. Click the  Settings button in the Startup and Recovery section. Look to see if the  windows server 2003 is listed on the dropdown menu. If so, check the box  next to "time to display list of operating systems" and choose a number  in the box next to it. Click ok, restart your computer, and choose  windows server 2003. If it didn't appear on the dropdown menu, click the  edit buttion to manually edit boot.ini and add an entry for server 2003  with the correct partition information (if you don't know the partition  number, copy the entry for xp and change partition(x) to 1, try  rebooting, and keep increasing the number until you find what partition  it is on.

Windows boots just fine under it's own power so why mess around with it?

I assume it also booted properly using the old Karmic legacy grub.

---

### Post by bitburger on 2010-06-08
> **kansasnoob said:**
> Windows boots just fine under it's own power so why mess around with it?

I assume it also booted properly using the old Karmic legacy grub.

Yes it has been working before with Karmic legacy grub but it was a while ago and I have since reinstalled Win xP.

Below is my current and full RESULT.txt
The custom entries are things I have tried after reading other posts on dual boot issues. These does not work however.

I'll post soon again when I hav reinstalled grub 2 on both sda and sdb.

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
 => Grub 2 is installed in the MBR of /dev/sdd and looks on the same drive in 
    partition #1 for /boot/grub.
 => No known boot loader is installed in the MBR of /dev/sde

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       xfs
    Boot sector type:  -
    Boot sector info:  
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

sdd1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdd2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdd5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sde1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 10.0 GB, 10005037056 bytes
255 heads, 63 sectors/track, 1216 cylinders, total 19541088 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    15,888,284    15,888,222  83 Linux
/dev/sda2          15,888,285    19,535,039     3,646,755   5 Extended
/dev/sda5          15,888,348    16,450,559       562,212  82 Linux swap / Solaris
/dev/sda6          16,450,623    19,535,039     3,084,417  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   488,392,064   488,392,002   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63 1,953,520,064 1,953,520,002   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *          2,048   224,827,391   224,825,344  83 Linux
/dev/sdd2         224,829,438   234,440,703     9,611,266   5 Extended
/dev/sdd5         224,829,440   234,440,703     9,611,264  82 Linux swap / Solaris


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sde1                  63   488,392,064   488,392,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        00e12e66-337b-4cfa-aa35-3a4b8371db19   ext3                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        5160fe4b-a09a-475a-8af0-a3fee887362a   swap                                     
/dev/sda6        195e5e57-68b2-4f52-b57a-5e09b5f36c71   xfs                                      
/dev/sda: PTTYPE="dos" 
/dev/sdb1        B4E065B8E065820A                       ntfs                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        886896FB6896E76A                       ntfs       Storage                       
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        9ca9e059-703b-47f4-8ca0-a19811ef65a1   ext4                                     
/dev/sdd2: PTTYPE="dos" 
/dev/sdd5        0f71dbcc-f3b5-483a-91de-cacd122c767c   swap                                     
/dev/sdd: PTTYPE="dos" 
/dev/sde1        66CC327ACC324519                       ntfs       Storage                       
/dev/sde: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdd1        /                        ext4       (rw,errors=remount-ro)
/dev/sdb1        /media/c_drive           fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sde1        /media/e_storage         fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdc1        /media/d_storage         fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda1/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        20

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=00e12e66-337b-4cfa-aa35-3a4b8371db19 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=00e12e66-337b-4cfa-aa35-3a4b8371db19

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Microsoft Windows XP Professional
rootnoverify    (hd1,0)
savedefault
makeactive
map        (hd1) (hd0)
map        (hd0) (hd1)
chainloader    +1

title        Ubuntu 9.10, kernel 2.6.31-14-generic
uuid        00e12e66-337b-4cfa-aa35-3a4b8371db19
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=00e12e66-337b-4cfa-aa35-3a4b8371db19 ro quiet
initrd        /boot/initrd.img-2.6.31-14-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid        00e12e66-337b-4cfa-aa35-3a4b8371db19
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=00e12e66-337b-4cfa-aa35-3a4b8371db19 ro  single
initrd        /boot/initrd.img-2.6.31-14-generic

title        Ubuntu 9.10, kernel 2.6.28-16-generic
uuid        00e12e66-337b-4cfa-aa35-3a4b8371db19
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=00e12e66-337b-4cfa-aa35-3a4b8371db19 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-16-generic
quiet

title        Ubuntu 9.10, kernel 2.6.28-16-generic (recovery mode)
uuid        00e12e66-337b-4cfa-aa35-3a4b8371db19
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=00e12e66-337b-4cfa-aa35-3a4b8371db19 ro  single
initrd        /boot/initrd.img-2.6.28-16-generic

title        Ubuntu 9.10, memtest86+
uuid        00e12e66-337b-4cfa-aa35-3a4b8371db19
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=00e12e66-337b-4cfa-aa35-3a4b8371db19 /               ext3    errors=remount-ro 0       1
# /var/lib was on /dev/sda6 during installation
UUID=195e5e57-68b2-4f52-b57a-5e09b5f36c71 /var/lib        xfs     defaults        0       2
# swap was on /dev/sda5 during installation
UUID=5160fe4b-a09a-475a-8af0-a3fee887362a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


   5.7GB: boot/grub/menu.lst
   5.6GB: boot/grub/stage2
   6.2GB: boot/initrd.img-2.6.28-16-generic
   5.7GB: boot/initrd.img-2.6.31-14-generic
   5.7GB: boot/vmlinuz-2.6.28-16-generic
   6.1GB: boot/vmlinuz-2.6.31-14-generic
   5.7GB: initrd.img
   6.2GB: initrd.img.old
   6.1GB: vmlinuz
   5.7GB: vmlinuz.old

================================ sdb1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn 

=========================== sdd1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd3,1)'
search --no-floppy --fs-uuid --set 9ca9e059-703b-47f4-8ca0-a19811ef65a1
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd3,1)'
search --no-floppy --fs-uuid --set 9ca9e059-703b-47f4-8ca0-a19811ef65a1
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd3,1)'
    search --no-floppy --fs-uuid --set 9ca9e059-703b-47f4-8ca0-a19811ef65a1
    linux    /boot/vmlinuz-2.6.32-22-generic-pae root=UUID=9ca9e059-703b-47f4-8ca0-a19811ef65a1 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd3,1)'
    search --no-floppy --fs-uuid --set 9ca9e059-703b-47f4-8ca0-a19811ef65a1
    echo    'Loading Linux 2.6.32-22-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-22-generic-pae root=UUID=9ca9e059-703b-47f4-8ca0-a19811ef65a1 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd3,1)'
    search --no-floppy --fs-uuid --set 9ca9e059-703b-47f4-8ca0-a19811ef65a1
    linux    /boot/vmlinuz-2.6.32-21-generic-pae root=UUID=9ca9e059-703b-47f4-8ca0-a19811ef65a1 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd3,1)'
    search --no-floppy --fs-uuid --set 9ca9e059-703b-47f4-8ca0-a19811ef65a1
    echo    'Loading Linux 2.6.32-21-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-21-generic-pae root=UUID=9ca9e059-703b-47f4-8ca0-a19811ef65a1 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd3,1)'
    search --no-floppy --fs-uuid --set 9ca9e059-703b-47f4-8ca0-a19811ef65a1
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd3,1)'
    search --no-floppy --fs-uuid --set 9ca9e059-703b-47f4-8ca0-a19811ef65a1
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu 9.10, kernel 2.6.31-14-generic (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 00e12e66-337b-4cfa-aa35-3a4b8371db19
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=00e12e66-337b-4cfa-aa35-3a4b8371db19 ro quiet
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode) (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 00e12e66-337b-4cfa-aa35-3a4b8371db19
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=00e12e66-337b-4cfa-aa35-3a4b8371db19 ro single
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.28-16-generic (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 00e12e66-337b-4cfa-aa35-3a4b8371db19
    linux /boot/vmlinuz-2.6.28-16-generic root=UUID=00e12e66-337b-4cfa-aa35-3a4b8371db19 ro quiet splash
    initrd /boot/initrd.img-2.6.28-16-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.28-16-generic (recovery mode) (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 00e12e66-337b-4cfa-aa35-3a4b8371db19
    linux /boot/vmlinuz-2.6.28-16-generic root=UUID=00e12e66-337b-4cfa-aa35-3a4b8371db19 ro single
    initrd /boot/initrd.img-2.6.28-16-generic
}
menuentry "Ubuntu 9.10, memtest86+ (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 00e12e66-337b-4cfa-aa35-3a4b8371db19
    linux /boot/memtest86+.bin 
}
menuentry "Microsoft Windows XP Professional (on /dev/sdb1)" {
    insmod ntfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set b4e065b8e065820a
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "My Win XP (on /dev/sdb1)" {
        insmod ntfs
        set root='(hd1,0)'
        search --no-floppy --fs-uuid --set b4e065b8e065820a
    drivemap -s (hd0) ${root}
        chainloader +1
}

menuentry "My Win XP test witout drivemap (on /dev/sdb1)" {
        insmod ntfs
        set root='(hd1,0)'
        search --no-floppy --fs-uuid --set b4e065b8e065820a
        chainloader +1
}
### END /etc/grub.d/40_custom ###

=============================== sdd1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdd1 during installation
UUID=9ca9e059-703b-47f4-8ca0-a19811ef65a1 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdd5 during installation
UUID=0f71dbcc-f3b5-483a-91de-cacd122c767c none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sdb1       /media/c_drive    ntfs  defaults,nls=iso8859-1,uid=1000,gid=1000,umask=0077,dir_mode=0700,file_mode=0600 0  0  
/dev/sde1       /media/e_storage  ntfs  defaults,nls=iso8859-1,uid=1000,gid=1000,umask=0077,dir_mode=0700,file_mode=0600 0  0  
/dev/sdc1       /media/d_storage  ntfs  defaults,nls=iso8859-1,uid=1000,gid=1000,umask=0022,dir_mode=0755,file_mode=0644 0  0  
#/dev/sdf1       /media/g_external ntfs  defaults,nls=iso8859-1,uid=1000,gid=1000,umask=0077,dir_mode=0700,file_mode=0600 0  0

=================== sdd1: Location of files loaded by Grub: ===================


  21.6GB: boot/grub/core.img
  13.1GB: boot/grub/grub.cfg
  21.7GB: boot/initrd.img-2.6.32-21-generic-pae
  21.7GB: boot/initrd.img-2.6.32-22-generic-pae
  21.6GB: boot/vmlinuz-2.6.32-21-generic-pae
  21.7GB: boot/vmlinuz-2.6.32-22-generic-pae
  21.7GB: initrd.img
  21.7GB: initrd.img.old
  21.7GB: vmlinuz
  21.6GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sde

00000000  90 e9 7d 01 fa 33 c0 8e  d0 8e c0 8e d8 bc 00 7c  |..}..3.........||
00000010  8b f4 fb bf 00 06 b9 00  01 f3 a5 bb 20 06 ff e3  |............ ...|
00000020  90 90 be 7d 07 81 3c aa  55 75 11 e8 58 00 73 0c  |...}..<.Uu..X.s.|
00000030  e8 65 00 72 07 e8 b1 00  72 3b eb 2c be 7d 07 c7  |.e.r....r;.,.}..|
00000040  04 00 00 ba 80 00 be be  07 b9 04 00 f6 04 80 75  |...............u|
00000050  07 83 c6 10 e2 f6 eb 1d  8a 74 01 8b 4c 02 bb 00  |.........t..L...|
00000060  7c b8 01 02 cd 13 72 0d  81 3e fe 7d 55 aa 75 05  ||.....r..>.}U.u.|
00000070  ea 00 7c 00 00 be 6a 07  ac 0a c0 74 fe bb 07 00  |..|...j....t....|
00000080  b4 0e cd 10 eb f2 bb 00  7e c6 07 13 c6 47 01 00  |........~....G..|
00000090  b2 80 b8 00 e0 cd 13 c3  bf 00 7e ba f0 01 b3 a0  |..........~.....|
000000a0  e8 84 00 72 0c b1 01 e8  48 00 72 05 e8 19 00 73  |...r....H.r....s|
000000b0  16 f6 c3 10 75 05 80 cb  10 eb e5 81 fa 70 01 74  |....u........p.t|
000000c0  05 ba 70 01 eb d8 f9 c3  81 bd fe 01 55 aa 75 17  |..p.........U.u.|
000000d0  8b 75 02 81 fe be 01 77  0e 03 f7 81 3c aa 55 75  |.u.....w....<.Uu|
000000e0  06 f6 44 02 01 75 01 f9  c3 bf 00 7c b1 0a e8 01  |..D..u.....|....|
000000f0  00 c3 52 57 83 c2 02 b0  01 ee 42 8a c1 ee 42 32  |..RW......B...B2|
00000100  c0 ee 42 ee 42 8a c3 ee  42 b0 20 ee e8 33 00 ec  |..B.B...B. ..3..|
00000110  24 fd 3c 58 75 0d 83 ea  07 b9 00 01 fa f3 6d fb  |$.<Xu.........m.|
00000120  f8 eb 01 f9 5f 5a c3 52  83 c2 07 ec a8 80 75 0f  |...._Z.R......u.|
00000130  4a 8a c3 ee 42 ec 24 d0  3c 50 75 03 f8 eb 01 f9  |J...B.$.<Pu.....|
00000140  5a c3 51 8b 0e 6c 04 83  c1 12 81 c2 ff 01 ec 8a  |Z.Q..l..........|
00000150  e0 80 e4 d8 80 fc 58 74  06 3b 0e 6c 04 75 ef 81  |......Xt.;.l.u..|
00000160  ea ff 01 b9 00 20 e2 fe  59 c3 0d 0a 45 72 72 6f  |..... ..Y...Erro|
00000170  72 20 4c 6f 61 64 69 6e  67 20 4f 53 00 aa 55 00  |r Loading OS..U.|
00000180  00 e9 80 fe 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  6b e1 02 ad 00 00 00 01  |........k.......|
000001c0  01 00 07 fe ff ff 3f 00  00 00 42 45 1c 1d 00 00  |......?...BE....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdd2

00000000  c8 16 aa d2 ed ed bf b2  80 a5 a6 90 eb c8 b6 0d  |................|
00000010  3d 53 49 37 c3 be 55 4d  98 86 5b a4 24 35 24 78  |=SI7..UM..[.$5$x|
00000020  2c f9 a0 ed d5 c6 7c b4  2b 1f 94 13 d3 c0 38 dd  |,.....|.+.....8.|
00000030  f9 2d 59 85 62 bd d4 fe  3b 9e 3e ab a9 4f 01 12  |.-Y.b...;.>..O..|
00000040  8b 9e 89 80 82 8e 56 08  df 59 b3 03 d8 e7 d2 23  |......V..Y.....#|
00000050  7e 81 83 75 c5 0c ee cd  04 c6 56 f9 ad 85 d1 09  |~..u......V.....|
00000060  7c 3c 6b 8a 73 6e 35 03  dc 85 c3 15 a6 b0 b6 ec  ||<k.sn5.........|
00000070  60 b6 c1 99 c7 59 1e b0  8d 66 37 34 55 76 b1 d0  |`....Y...f74Uv..|
00000080  29 09 41 e8 5a 00 d2 34  bf 85 4d a9 6b c5 d5 65  |).A.Z..4..M.k..e|
00000090  f6 9c 7a 89 a0 6a a9 af  bc 96 02 83 8e fb 36 ba  |..z..j........6.|
000000a0  3c 0f 1a 61 52 1e 81 3d  f9 ca 56 77 c9 14 56 e5  |<..aR..=..Vw..V.|
000000b0  13 09 a4 90 c1 ff 7c 58  d7 9f 32 3a 43 7c 52 ae  |......|X..2:C|R.|
000000c0  d8 ec 91 80 db e1 61 f5  52 a6 3e 92 f5 fc 18 40  |......a.R.>....@|
000000d0  ec 9c 2b 30 31 81 0e 5c  ad 9b d4 60 ec c4 6b 91  |..+01..\...`..k.|
000000e0  8d 25 e5 3d af 86 e8 60  dc 37 1a 68 ad 10 43 1b  |.%.=...`.7.h..C.|
000000f0  1a a3 33 0f 6a d3 67 4a  ce 05 d3 fb 44 47 49 ac  |..3.j.gJ....DGI.|
00000100  01 93 90 70 f5 19 40 e3  33 ac 01 46 15 f9 84 68  |...p..@.3..F...h|
00000110  af b0 9a 69 37 55 dc c0  d5 64 8c d3 2e c6 14 ee  |...i7U...d......|
00000120  b3 50 0c 0a 8a 60 da d8  42 c9 67 9d 2c 36 49 9d  |.P...`..B.g.,6I.|
00000130  d6 03 a8 38 04 d8 de 3c  00 41 98 d5 39 cd 85 c2  |...8...<.A..9...|
00000140  77 64 d9 77 69 13 82 df  b0 fc 01 f5 3a 26 66 56  |wd.wi.......:&fV|
00000150  85 cc 78 7c d2 e1 cc e1  6c 46 66 76 04 2b 0e 5e  |..x|....lFfv.+.^|
00000160  02 2f 8f 14 ed 5e 83 3b  0c 22 d8 db e0 46 fe f3  |./...^.;."...F..|
00000170  27 43 a6 17 c7 27 ab 49  d7 8b dc c3 7b a2 dd 38  |'C...'.I....{..8|
00000180  6c 8a fc a3 a3 37 6e e8  14 70 15 13 2e 10 27 5e  |l....7n..p....'^|
00000190  b7 4f 87 d3 cd 81 a2 c4  d2 9c ac b6 77 af 41 a0  |.O..........w.A.|
000001a0  0d 02 01 00 a0 04 32 24  02 d5 09 3f 77 13 c1 32  |......2$...?w..2|
000001b0  68 ab a0 b3 27 c7 af 5e  1a ef 47 a3 b4 4b 00 fe  |h...'..^..G..K..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 a8 92 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



```

---

### Post by bitburger on 2010-06-08
So i reinstalled grub to both sda and sdd.

I still cannot boot into win xp, same error. I tried with both sda and sdd as first boot drive.

I can however now boot into ubuntu 9.10 that is on sda if I use sda as first boot drive.

I can still boot into 10.04 (on sdd) both using sda and sdd as first boot drive.

---

### Post by kansasnoob on 2010-06-09
> **bitburger said:**
> So i reinstalled grub to both sda and sdd.

I still cannot boot into win xp, same error. I tried with both sda and sdd as first boot drive.

I can however now boot into ubuntu 9.10 that is on sda if I use sda as first boot drive.

I can still boot into 10.04 (on sdd) both using sda and sdd as first boot drive.

Just curious, where you say:

> I can however now boot into ubuntu 9.10 that is on sda if I use sda as first boot drive.

Is that correct? Or do you mean you can NOT boot 9.10 with sda set as boot drive? I would now think you'd have to boot 9.10 using 10.04's grub 2.

Something I should take time to point out is that grub 2 still counts drives beginning with zero, but now begins counting partitions with one, so sdb1 = (hd1,1) in grub 2 whereas it would be (hd1,0) in legacy grub.

Anyway I've been studying a bit:

[http://grub.enbug.org/ChainLoadWindows](http://grub.enbug.org/ChainLoadWindows)

[http://en.gentoo-wiki.com/wiki/Grub2#Microsoft_Windows_Entry](http://en.gentoo-wiki.com/wiki/Grub2#Microsoft_Windows_Entry)

So based on that I'd try the following "custom" entries:

```
menuentry "Windows XP" {
    insmod chain
    insmod ntfs
    search --fs-uuid --set b4e065b8e065820a
    chainloader +1
}
```

Or:

```
menuentry "Microsoft Windows XP" {
    insmod chain
    insmod ntfs
    set root=(hd1)
    devicemap -s (hd3) (hd1)
    chainloader +1
}
```

You'll notice in that last entry I'm using only the drive designation as "set root" instead of drive and partition. Also I'm using parenthesis in "devicemap -s". Possibly even NOT using the parenthesis may be better but I don't think so.

Also since I'm mapping hd3 and hd1 (The 10.04 drive and the Windows drive) I'm assuming you'll have sdd set as the boot drive. Am I helping or just confusing you more :confused:

Anyway, I dug up an old thread where I remembered installing grub 2 to the mbr of a Windows drive then made Windows bootable with the auto-generated grub entry:

[http://ubuntuforums.org/showthread.php?t=1384618](http://ubuntuforums.org/showthread.php?t=1384618)

His drive layout was different (Windows was on sdd1 and the Ubuntu with grub 2 was on sda1), but after trying many mapping combinations simply installing grub 2 to the MBR of the Windows drive worked. I've seen that on many occasions.

In fact I quite often install grub 2 to the MBR of all drives with Linux or Windows operating systems installed but I know very easily how to recover any Linux or Windows MBR with any Live CD:

[http://ubuntuforums.org/showpost.php?p=9338226&postcount=41](http://ubuntuforums.org/showpost.php?p=9338226&postcount=41)

Note: as soon as I'm done reviewing yesterdays threads I need to test that for typos.

Anyway I hope this gives you more ideas :)

---

### Post by bitburger on 2010-06-09
> **kansasnoob said:**
> 
Is that correct? Or do you mean you can NOT boot 9.10 with sda set as boot drive? I would now think you'd have to boot 9.10 using 10.04's grub 2.


Yes that was correct what I wrote, if I have sdd (10.04) as boot drive an choose the 9.10 menu entry I get something like
device not found <and the device id>
file not found
booting 9.10 is not my top prio however.

> **kansasnoob said:**
> 
Anyway I've been studying a bit:

[http://grub.enbug.org/ChainLoadWindows](http://grub.enbug.org/ChainLoadWindows)

[http://en.gentoo-wiki.com/wiki/Grub2#Microsoft_Windows_Entry](http://en.gentoo-wiki.com/wiki/Grub2#Microsoft_Windows_Entry)

I'll read these more carefully tomorrow and see if I can come up withe any combinations of my own.
For now I tested the entries you suggested.

> **kansasnoob said:**
> 
```
menuentry "Windows XP" {
    insmod chain
    insmod ntfs
    search --fs-uuid --set b4e065b8e065820a
    chainloader +1
}
```

This just gave me a blinking cursor and I had to Ctrl+Alt+Delete

> **kansasnoob said:**
> 
```
menuentry "Microsoft Windows XP" {
    insmod chain
    insmod ntfs
    set root=(hd1)
    devicemap -s (hd3) (hd1)
    chainloader +1
}
```
This gave me the message

"Reboot and Select proper Boot device
or Insert Boot Media in selected Boot device and press a key"

after pressing "a key" I got back to the grub menu.

> **kansasnoob said:**
> 
You'll notice in that last entry I'm using only the drive designation as "set root" instead of drive and partition. Also I'm using parenthesis in "devicemap -s". Possibly even NOT using the parenthesis may be better but I don't think so.

Also since I'm mapping hd3 and hd1 (The 10.04 drive and the Windows drive) I'm assuming you'll have sdd set as the boot drive. Am I helping or just confusing you more

I am still following you and I have actually tried similar things to this before but not these exact combinations.


> **kansasnoob said:**
> 
In fact I quite often install grub 2 to the MBR of all drives with Linux or Windows operating systems installed but I know very easily how to recover any Linux or Windows MBR with any Live CD:

I'll read more on the links you provided and if I feel brave this weekend I'll try to install grub to the Win MBR.
I just so bad wanted to not mess with the windows drive. I guess if it is as easy as you say to restore the Win MBR I might as well give it a try.

Thanks again

---

### Post by kansasnoob on 2010-06-09
Feel free to send me a brief PM pointing me back here when you decide to play with this some more.

There are undoubtedly some corner issues where grub 2 still doesn't work well and if all else fails we can revert you to using legacy grub:

[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

But I'd really appreciate you trying to work through this with grub 2 if you don't mind playing.

---

### Post by kansasnoob on 2010-06-09
BTW this:

> Yes that was correct what I wrote, if I have sdd (10.04) as boot drive an choose the 9.10 menu entry I get something like
device not found <and the device id>
file not found
booting 9.10 is not my top prio however.

Definitely makes this sound like a drive mapping issue so IMHO this is a bug in grub 2 or it's device mapping.

---

### Post by oldfred on 2010-06-10
I boot with grub2 from sdc. I also have grub2 in sda to boot Lucid.

While Karmic or Lucid consider my drives as sda, sdb & sdc as the same drive, grub will not let me chainboot to sda with hd0 which I would think should be the first drive. But because I boot sdc grub must think that sdc is hd0 and my chainboot to hd1 then works. 

My device map matches my drive order and I cannot find a device.map in Lucid.

So for grub the boot device may change the hd0, hd1 drive order. I just tried alternates until one worked. And I think this would apply to a chainboot to windows.

---

### Post by bitburger on 2010-06-10
Thanks for all your help. I have some ideas i want to try and will post when i am done.

---

