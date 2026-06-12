---
title: "Problem with dual boot"
date: 2010-06-24
forum: General Help
---

### Post by curambar on 2010-06-24
I had Windows XP SP3. So, I tried to make a dual boot install of Xubuntu 9.10. Installation ran perfectly, and Xubuntu runs smoothly. But now I can't boot windows anymore.

Let's start with the fdisk -l dump:
```
Disco /dev/sda: 40.0 GB, 40020664320 bytes
255 cabezas, 63 sectores/pista, 4865 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0xd4b0d4b0

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *         707        3950    26057398+   7  HPFS/NTFS
/dev/sda2            3951        4819     6980242+  83  Linux
/dev/sda3               2         706     5662912+   f  W95 Ext'd (LBA)
/dev/sda4            4820        4865      369495   82  Linux swap / Solaris
/dev/sda5               2         706     5662881    7  HPFS/NTFS

Las entradas de la tabla de particiones no están en el orden del disco

```
Yes, I'm from Argentina, so I'm using Xubuntu in spanish.
Judging by the sizes, sda1 is my data partition (where i keep music, files, etc), and sda5 is the windows XP OS partition.

Thing is, after I installed xubuntu, GRUB gives me the option to boot from Win XP, as expected. But when I select that option, it says something like this (i'm translating it back to english):
```
Windows XP won't load, because the following file is missing or corrupt:
<windows root>\system32\hal.dll
Install a copy of the file
```

The corresponding part of grub.cfg displays this text:
```

    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 0638cc9438cc8461
    drivemap -s (hd0) ${root}
    chainloader +1
```
I tried to change it to (hd0,0) and/or (hd0,4) but it's still not working.

Ideas?

---

### Post by VH-BIL on 2010-06-24
Try:
```
sudo update-grub2
```
or
```
sudo update-grub
```
depending on what version of grub you have.

---

### Post by arrange on 2010-06-24
The message *Windows XP won't load...* is from Windows, not from Ubuntu or Grub, and is _probably_ not related to your Xubuntu install.
Can you see the *hal.dll* file from Xubuntu?
Can you post the output of [boot_info_script]("https://sourceforge.net/projects/bootinfoscript/")? (If you don't know how to run the script, [look here]("http://bootinfoscript.sourceforge.net/").)

---

### Post by mikewhatever on 2010-06-24
curambar, hi and welcome.
In case Windows is installed on sda5 and sda1 is a data partition, I'd have to say that your hdd is rather messy.
Check out the link below for the explanation on 'hal.dll missing' error.
[http://members.iinet.net.au/~herman546/p15.html#hal.dll_is_missing_or_corrupt](http://members.iinet.net.au/~herman546/p15.html#hal.dll_is_missing_or_corrupt)
Look for the boot.ini file on sda1 and, if you need help, post it here for review.

Edit: Windows keeps its boot files on the first primary partition, so that (hd0,1) in grub.cfg is correct.

---

### Post by curambar on 2010-06-24
Thanks, people, but I still can't load that damn partition.

I ran boot_info_script, and this is the output:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows XP
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disco /dev/sda: 40.0 GB, 40020664320 bytes
255 cabezas, 63 sectores/pista, 4865 cilindros, 78165360 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Identificador de disco: 0xd4b0d4b0

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *     11,341,953    63,456,749    52,114,797   7 HPFS/NTFS
/dev/sda2          63,456,750    77,417,234    13,960,485  83 Linux
/dev/sda3              16,065    11,341,889    11,325,825   f W95 Ext d (LBA)
/dev/sda5              16,128    11,341,889    11,325,762   7 HPFS/NTFS
/dev/sda4          77,417,235    78,156,224       738,990  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        0638CC9438CC8461                       ntfs       DATA PACK                     
/dev/sda2        70292107-2468-4697-8924-dc291b3ef9df   ext4                                     
/dev/sda4        669c0c71-238e-4f24-b9cb-d229ca55e405   swap                                     
/dev/sda5        2CCC43CECC4390CE                       ntfs                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda2        /                        ext4       (rw,errors=remount-ro)
/dev/sda1        /mnt/winos               fuseblk    (rw,nosuid,nodev,allow_other,blksize=2048)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=0 
default=multi(0)disk(0)rdisk(0)partition(4)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(4)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /TUTag=1UC9W4 /Kernel=TUKernel.exe 
multi(0)disk(0)rdisk(0)partition(4)\WINDOWS="Microsoft Windows XP Professional (TuneUp Backup)" /noexecute=optin /fastdetect /TUTag=1UC9W4-BAK 

=========================== sda2/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,2)
search --no-floppy --fs-uuid --set 70292107-2468-4697-8924-dc291b3ef9df
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-22-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 70292107-2468-4697-8924-dc291b3ef9df
    linux    /boot/vmlinuz-2.6.31-22-generic root=UUID=70292107-2468-4697-8924-dc291b3ef9df ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-22-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 70292107-2468-4697-8924-dc291b3ef9df
    linux    /boot/vmlinuz-2.6.31-22-generic root=UUID=70292107-2468-4697-8924-dc291b3ef9df ro single 
    initrd    /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 70292107-2468-4697-8924-dc291b3ef9df
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=70292107-2468-4697-8924-dc291b3ef9df ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 70292107-2468-4697-8924-dc291b3ef9df
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=70292107-2468-4697-8924-dc291b3ef9df ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,4)
    search --no-floppy --fs-uuid --set 0638cc9438cc8461
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=70292107-2468-4697-8924-dc291b3ef9df /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda4 during installation
UUID=669c0c71-238e-4f24-b9cb-d229ca55e405 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/hda1 /media/datos ntfs-fuse auto,gid=1001,umask=0002 0 0

=================== sda2: Location of files loaded by Grub: ===================


  33.0GB: boot/grub/core.img
  33.0GB: boot/grub/grub.cfg
  34.4GB: boot/initrd.img-2.6.31-14-generic
  35.3GB: boot/initrd.img-2.6.31-22-generic
  32.9GB: boot/vmlinuz-2.6.31-14-generic
  35.0GB: boot/vmlinuz-2.6.31-22-generic
  35.3GB: initrd.img
  34.4GB: initrd.img.old
  35.0GB: vmlinuz
  32.9GB: vmlinuz.old
```Anyways, I looked at that site about hal.dll, and it says the problem may be in the 'boot.ini' file. I tried to change that so it has another partition (in the code above, I was trying partition 4), but I can't make it. I tried already with these options.
multi(0)disk(0)rdisk(0)partition(0)\WINDOWS  
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS  
multi(0)disk(0)rdisk(0)partition(4)\WINDOWS  

Is it that I have to put the correct grub.cfg / boot.ini combination for the partition numbers? If so, what partition number should I put in each one of them?

Sorry for being so annoying, I just want my win back too :p

EDIT!!!
I just found the problem... As mikewhatever said, my HD is quite messy. The problem is that the boot.ini is in SDA1, but windows itself is in SDA5... I will try to see if I can work from that... anyways, if you can help me, it will be very nice of you :p

---

### Post by oldfred on 2010-06-24
Grub2 & windows number drives from 0 and partitions from 1. 
sda1 is drive 0 partition 1 or in windows disk 0 partition 1

This is my XP entry for sda1
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

---

### Post by warfacegod on 2010-06-24
> **VH-BIL said:**
> Try:
```
sudo update-grub2
```
or
```
sudo update-grub
```
depending on what version of grub you have.

I've got GRUB2 ( 1.98 ) and I have never needed to use update-grub2. In fact I've never even heard of it. From what I understand update-grub is supposed to become grub-mkconfig sometime soon. Don't know why. It seems like a stupid change to me.

Sorry for the interruption, OP.

---

### Post by oldfred on 2010-06-24
Once the question of grub or grub2 came up I checked my system. the update-grub2 calls update-grub and update-grub calls the grub-mkconfig. So they all are the same thing.

---

### Post by curambar on 2010-06-24
Ok, people, the boot.ini fixed some portion of the problem... Now I can actually access the windows boot menu.

This is what I did:
1) I added some menu time to boot.ini, and there it was, the boot menu.
2) I changed boot.ini so it reads partition 5

So, now, it actually tries to do something different, it no longer says anything about hal.dll, but now I have a different error:
```
 Windows could not start because of a computer_ _disk hardware configuration problem.
Could not read from the selected boot disk[[COLOR=#05408f][/COLOR]]("http://www.techspot.com/vb/topic11762.html#"). Check boot path and disk hardware. Please check the Windows documentation about hardware disk configuration and your hardware reference manuals for additional information.
```I have read something in windows forums, but they all say "reinstall windows and stop whining". I have not seen a good option for dual boots. I'm trying to see if there's some other option before trying that (because I don't have my win CD here, and I will get it on saturday). Anyways, if that was the case, I suppose I would have to reinstall windows and then reinstall grub... 

Could it be something MBR related? Is there some fix tool I could use? I have a recovery cd named "HIREN Boot CD 9.9", anyone knows if is there such a tool in there?

---

### Post by oldfred on 2010-06-24
Your windows in sda5 has no boot files. Just because the boot type is XP does not mean it has a system, it just may be a NTFS data partition.

The only partition with boot files is sda1. Did you have additional windows installs?

---

### Post by varunendra on 2010-06-25
> **oldfred said:**
> Your windows in sda5 has no boot files. Just because the boot type is XP does not mean it has a system, it just may be a NTFS data partition.

The only partition with boot files is sda1. Did you have additional windows installs?

@curambar,

Considering the above quote of oldfred, if you have a bootable WinXP installation CD, boot from it, select install at the first prompt (where it says: ENTER to install now, R to recover, F3 to quit).
Then it will search entire hard disk for any previous installation. If you have your WinXP installation still intact, it will be detected & listed up in the search result & you'll be asked if you want to repair it.
At this point, you can either press R to recover & get it working again (not guaranteed, GRUB would be lost too, but can be restored later) or you can simply quit pressing F3 and proceed to other resolutions.
You should also check if you have the 'Windows' directory in sda5. If it is not there, you have no Windows setup there (unless you or some win-installer program had intentionally changed the installation directory name to something else during Win installation).

From your last post, I'm assuming you would have edited your boot.ini file so that it now looks something like:```
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(5)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(5)\WINDOWS="Microsoft Windows XP Professional" /noexecute /fastdetect
```[COLOR=DarkRed]NOTE: This is how my boot.ini file looks like. Whereas in your boot.ini file, the booting job is handed over to something called TUKernel.exe. This **may be** a reason for the problem but I'm not sure as I've never come across a scenario where booting in XP ends up upon anything other than kernel32.dll.
I'd suggest to try changing it to look like mine (with /noexecute /fastdetect being the only parameters)[/COLOR]
Please note that once you come up to WinXP boot menu, the role of GRUB or GRUB2 is finished. If the booting fails after that, there must be something wrong with Windows boot files (boot.ini, ntldr, ntdetect.com, kernel32.dll) or their configuration. Linux or GRUB has no part to play in it.

---

### Post by oldfred on 2010-06-25
Because the XP partition is in sda5 which is  a logical partition the repair CD may not even find it. Windows prefers primary partitions. It does combine booting of the second install into the first install and moves some boot files, but I would expect to see some files in the extended partition.

---

### Post by varunendra on 2010-06-25
> **oldfred said:**
> Because the XP partition is in sda5 which is  a logical partition the repair CD may not even find it. Windows prefers primary partitions. It does combine booting of the second install into the first install and moves some boot files, but I would expect to see some files in the extended partition.

With all due respect, I want to politely disagree with you at this point. I have installed XP in logical drives in the past. The one & only primary partitions in those setups used to be FAT or FAT32 holding DOS or Win98.
I also had to use XP installation/repair CDs sometimes and they had no difficulty in detecting those installations. It is only the boot loader files of XP (boot.ini, ntldr and NTDETECT.com) that have to necessarily reside in the active partition (which are there in OP's sda1).

I've heard that Win7 does have some nonsense affection for primary partition, but for XP, I don't think there is any.

---

### Post by curambar on 2010-06-26
Ok, I cleaned up the partition mess, now I have only one NTFS partition, and 3 linux partitions (home, root, swap).
fdisk dump, just in case:
```
Disco /dev/sda: 40.0 GB, 40020664320 bytes
255 cabezas, 63 sectores/pista, 4865 cilindros, 78165360 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Identificador de disco: 0xd4b0d4b0

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *          63    52436159    26218048+   7  HPFS/NTFS
/dev/sda2        52436160    63456749     5510295   83  Linux
/dev/sda3        63456750    77417234     6980242+  83  Linux
/dev/sda4        77417235    78156224      369495   82  Linux swap / Solaris

```

now, boot.ini is working fine, it loads normally, and presents a reasonable list of options (namely, just plain, ol' windows, and a second copy of that, because I messed up and installed it twice :p)
@varunendra: TuKernel.exe was some TuneUp Utilities garbage, which was promptly erased.

I reinstalled Win XP in the NTFS partition, and, from Live CD, installed a copy of grub.
Now, I can still access the windows boot menu, and it *tries* to boot, but to no avail. It automatically reboots.
I tried to do a safe-mode boot from win. It starts loading a bunch of sys and dll files and then, wham, reboot. This happened AFTER I reinstalled grub.

waaarrgh, I'm starting to feel windows and xubuntu are natural enemies, and will start the armageddon before working peacefully together :p

---

### Post by varunendra on 2010-06-26
> **curambar said:**
> waaarrgh, I'm starting to feel windows and xubuntu are natural enemies, and will start the armageddon before working peacefully together :p
:D With a similar setup like yours (simulated over VMware) I have a different story to tell!:D
```

Disk /dev/sda: 42.9 GB, 42949672960 bytes
255 heads, 63 sectors/track, 5221 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x08160816

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         773     6209091    7  HPFS/NTFS
/dev/sda2             774        2078    10482412+  83  Linux
/dev/sda3            2079        4883    22531162+  83  Linux
/dev/sda4            4884        5221     2714985   82  Linux swap / Solaris

```

I had a preinstalled VMware image of XP (installed on a single-partition virtual HDD) VM. I booted it with xubuntu live, resized & repartitioned the HDD. Then I installed xubuntu on sda2 & made sda3 the mount-point for /home.
So the current setup is:
sda1 = XP
sda2 = xubuntu (/)
sda3 = /Home
sda4 = swap

Both XP & xubuntu are running perfectly! (WITHOUT STARTING ARMAGEDDON!!) :D

Please run the [boot info script again]("http://bootinfoscript.sourceforge.net/") & post the new results.

---

### Post by curambar on 2010-06-27
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda3 and 
                       looks at sector 66637222 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disco /dev/sda: 40.0 GB, 40020664320 bytes
255 cabezas, 63 sectores/pista, 4865 cilindros, 78165360 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Identificador de disco: 0xd4b0d4b0

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    52,436,159    52,436,097   7 HPFS/NTFS
/dev/sda2          52,436,160    63,456,749    11,020,590  83 Linux
/dev/sda3          63,456,750    77,417,234    13,960,485  83 Linux
/dev/sda4          77,417,235    78,156,224       738,990  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        A08B1FDB3BE4AC2F                       ntfs       WIN                           
/dev/sda2        f5172713-8044-45a9-b107-365e5ce3810e   ext4       HOME                          
/dev/sda3        70292107-2468-4697-8924-dc291b3ef9df   ext4                                     
/dev/sda4        669c0c71-238e-4f24-b9cb-d229ca55e405   swap                                     
/dev/sdb         5066-2189                              vfat       CUCHUFLO                      

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda3        /                        ext4       (rw,errors=remount-ro)
/dev/sda2        /media/home              ext4       (rw)
/dev/sda1        /mnt/win02               fuseblk    (ro,noexec,nosuid,nodev,allow_other,default_permissions,blksize=4096)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS.0 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS.0="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=========================== sda3/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,2)
search --no-floppy --fs-uuid --set 70292107-2468-4697-8924-dc291b3ef9df
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-22-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 70292107-2468-4697-8924-dc291b3ef9df
    linux    /boot/vmlinuz-2.6.31-22-generic root=UUID=70292107-2468-4697-8924-dc291b3ef9df ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-22-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 70292107-2468-4697-8924-dc291b3ef9df
    linux    /boot/vmlinuz-2.6.31-22-generic root=UUID=70292107-2468-4697-8924-dc291b3ef9df ro single 
    initrd    /boot/initrd.img-2.6.31-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows XP (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set A08B1FDB3BE4AC2F
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=70292107-2468-4697-8924-dc291b3ef9df /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda4 during installation
UUID=669c0c71-238e-4f24-b9cb-d229ca55e405 none            swap    sw              0       0
UUID=f5172713-8044-45a9-b107-365e5ce3810e /media/home    ext4    defaults 0 0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda1     /mnt/win02  ntfs     auto,ro,exec,users,dmask=000,fmask=111,nls=utf8  0       0

=================== sda3: Location of files loaded by Grub: ===================


  34.5GB: boot/grub/core.img
  33.0GB: boot/grub/grub.cfg
  34.4GB: boot/initrd.img-2.6.31-14-generic
  33.0GB: boot/initrd.img-2.6.31-22-generic
  32.9GB: boot/vmlinuz-2.6.31-14-generic
  35.0GB: boot/vmlinuz-2.6.31-22-generic
  33.0GB: initrd.img
  34.4GB: initrd.img.old
  35.0GB: vmlinuz
  32.9GB: vmlinuz.old
```

Just some things: The block of text in SDA2 I think is because I tried to reinstall grub in that partition by mistake once.
Oh, and I have two windows installs, because once it stopped working, instead of formatting and installing, I just installed windows on top of it. I thought it would overwrite the previous installation, but it installed a parallel one. Windows is a weird thing.

Well, symptoms: It *wants* to boot, it actually starts doing it. As I said before, it starts loading dlls and sys (in safe mode I can see the names of the files rolling at the bottom of the screen), and suddenly, it reboots, without previous warning.
I don't know what grub is doing with that partition, but once grub is installed, windows just stops working...

I'm about to give up, and work just with ubuntu... But really, it would be really sweet to have some of my win programs back. Yes, I know wine, but I have *really* low memory (192 M), and running a win application with an emulator is just... sad :p

Or, I'll just wait until I can buy a new computer ^_^

---

### Post by varunendra on 2010-06-27
Why don't you start from scratch? Just backup you data, delete all the partitions, & recreate everything with better understanding this time.

If it makes any sense to you, here's how you do it:

[LIST]
[*]Backup all your important data to an external media (thumb drive, dvd, etc.)
[*]Boot from LiveCD, open GParted, delete all the partitions.
[*]Create 4 new primary partitions (**1st- **(6-8GB) ntfs, **2nd-** (4-6GB) ext3/4, **3rd-** (all remaining space-2GB) ext3/4, **4th- **(2GB)swap).
[*]Reboot with XP installation CD. Start with installing XP in the first (ntfs) partition.
[*]Once XP is ready with all your favourite programs installed, take a compressed backup image of the whole partition (just in case you need to restore it).
[*]Install xubuntu in sda2, making sda3 a mount point for /home. Except for selecting the partition plan manually, go with all default options. (Please don't install Grub on some 'partition' this time :). It would be installed on MBR automatically as it should).
[/LIST]
Reboot & everything should be cool!

If you have some problem in implementing above, please mention here. Maybe suggesting a solution for that would be easier!
:cool:

---

