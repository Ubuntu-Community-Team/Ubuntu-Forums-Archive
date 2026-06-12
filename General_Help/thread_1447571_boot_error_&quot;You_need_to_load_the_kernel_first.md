---
title: "boot error &quot;You need to load the kernel first&quot;"
date: 2010-04-05
forum: General Help
---

### Post by mayapower on 2010-04-05
I am using kubuntu karmic 9.10. Yesterday night I did installed/uninstalled various things and unfortunately something went wrong.

Now the boot menu shows 2.6.31-20 generic/recovery, 2.6.31-19 generic/recovery and one more including windows one in the last.

*ALL* of the menu options, including recovery ones are producing an error saying:
"**You need to load the kernel first**"

My skills are limited on linux domain and I installed kubuntu using disk image.

Any help would greatly be appreciated.

Regards

Prashant

---

### Post by drs305 on 2010-04-05
If you can get to the Grub2 menu, you can enter the grub command line mode by pressing "c" and then booting manually. The procedures are located in the Grub 2 community doc:
[https://help.ubuntu.com/community/Grub2#Using%20CLI%20to%20Boot]("https://help.ubuntu.com/community/Grub2#Using%20CLI%20to%20Boot")

If you are able to boot after entering the commands detailed above, try running the following to update Grub 2:
```
sudo update-grub
```

If you are unable to successfully use the command line, boot the LiveCD and then run meierfra's boot info script so we can take a look at your system files:
[http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")

---

### Post by mayapower on 2010-04-05
I gave a try to solve the problem using grub menu but it didn't help. May be I was not able to do it properly.
Here is the results of bootinfoscript:
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr /wubildr

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/home.disk 
                       /ubuntu/disks/swap.disk

sda5/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sda6: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x22522251

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    40,965,749    40,965,687   7 HPFS/NTFS
/dev/sda2          40,965,750   156,280,319   115,314,570   f W95 Ext d (LBA)
/dev/sda5          40,965,813    81,931,499    40,965,687   c W95 FAT32 (LBA)
/dev/sda6          81,931,563   122,897,249    40,965,687   c W95 FAT32 (LBA)
/dev/sda7         122,897,313   156,280,319    33,383,007   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       26d59033-ba5c-493b-af82-e225dbb20de5   ext4                                     
/dev/ramzswap0                                          swap                                     
/dev/sda1        B6383AC2383A8203                       ntfs                                     
/dev/sda5        A057-B3F3                              vfat                                     
/dev/sda6        60C1-A239                              vfat                                     
/dev/sda7        F8C6-FFA2                              vfat                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
C:\wubildr.mbr = "Kubuntu"


```

---

### Post by ubun2warrior on 2010-04-06
I faced similar problems and as a novice myself could not do anything. So the best thing would be to reinstall Kubuntu. Just be careful so that u don't damage your important data(If any)

---

### Post by mayapower on 2010-04-06
Reinstalling would be my final option. Let's see if someone helps by seeing the result.txt.
I have so many application installed and configured. Is there any way to reinstalling the os and at the same time prevent the existing data. This is similar to repair option in windows.

Prashant

---

### Post by mayapower on 2010-04-06
Hey!

Do I have to re-install the os?


Prashant

---

### Post by lordskid on 2010-04-06
> **mayapower said:**
> Hey!

Do I have to re-install the os?


Prashant

don't just yet. select your desired option from the menu. then press 'e'
use the down arrow key... are you missing letter 'c' from the boot option?

it's the vmlinuz /boot/grub/vmlinuz.......-generic

well just add the 'c' and press control-x
and you should be good to go.

post back if this is the case.

---

### Post by mayapower on 2010-04-06
I don't see a line similar of yours.
How ever 6th line in boot script says:

```

linux /boot/vmlinuz-2.6.31-20-generic root=/dev/sda5 loop=/ubuntu/disks\root.disk ro quiet splash

```

Where do I add character "c".

Prashant

---

### Post by drs305 on 2010-04-06
For helpers, it is important to note that this is a Wubi install within the Windows partition. 

Your wubi 'partition' within Windows is not being mounted correctly. There is a known bug with Wubi. I don't know if it applies to your situation (I don't use Wubi) but it is worth trying. The solution is posted in this link -see if it resolves the problem:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10")

If you aren't able to fix the problem, you may still be able to inspect and recover any important files by mounting the Wubi install as follows if the file Wubi can be mounted:
Boot the LiveCD to the Desktop, then
```

sudo mkdir /windows
sudo mount /dev/sda1 /mnt/windows
sudo mkdir /mnt/vdisk
sudo mount -o loop /windows/ubuntu/disks/root.disk /mnt/vdisk

```

---

### Post by mayapower on 2010-04-06
Tell me how can I completely remove ubuntu and all related files from my computer.

---

### Post by drs305 on 2010-04-06
> **mayapower said:**
> Tell me how can I completely remove ubuntu and all related files from my computer.

You should be able to uninstall a Wubi installation via Windows Add/Remove application, since it is installed as a file/program within Windows.

Please don't let your experience with Wubi reflect badly on the entire Ubuntu OS. At some point you may want to try a normal installation of Ubuntu on its own partition. Not only is the OS more tested on a normal installation, there will be many more helpers who can assist when you do have questions.

---

### Post by mayapower on 2010-04-06
I tried couple of more times but nothing helped. I think I need to do a fresh installation. Please let me know how to uninstall the existing installation. I do have a dual boot with xp and I don't want to mess with xp installation.

Secondly this time I would prefer to use VirtualBox instead of default installation method.

Any pointers on this will greatly be appreciated.

Thanks

---

### Post by mayapower on 2010-04-06
[[COLOR=#D40000]**Dear drs305**[/COLOR]]("http://ubuntuforums.org/member.php?u=223945")

As far as I remember the very first time I tried installing kubuntu using wubi and failed because of some unknown reasons. I still remember correctly that later I downloaded the iso image and installed it using a CD. It may possible that I was not able to delete/uninstall previous wubi things properly.

I can understand that I might have done something wrong yesterday but being as a novice I need a more stable environment where if such things occurred, I might be able to sort things out instead of reinstalling the OS again.


Thanks

---

