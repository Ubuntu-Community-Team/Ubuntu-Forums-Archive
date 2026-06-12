---
title: "Urgent help-Can not see desktop icons!"
date: 2010-10-06
forum: General Help
---

### Post by gagea on 2010-10-06
Hello ubuntu users,

Somehow I can not see any of desktop icons, toolbars, etc. I restarted computer several times and I still have the same problem. My only issue is that I have important data in Documents in home. It is all of my today work+all the week. Please tell me how to retrieve those data. Your help really appreciated. 

Thanks, 

Gagea

---

### Post by drs305 on 2010-10-06
If the Desktop seems to have a piece of glass over it (can't right click on it, etc), open a terminal with ALT-F2, copy this and press ENTER:
```
gconftool-2 --type bool --set /apps/nautilus/preferences/show_desktop 'true'
```

---

### Post by gagea on 2010-10-06
> **drs305 said:**
> If the Desktop seems to have a piece of glass over it (can't right click on it, etc), open a terminal with ALT-F2, copy this and press ENTER:
```
gconftool-2 --type bool --set /apps/nautilus/preferences/show_desktop 'true'
```

Thanks,
Even with ALT-F2 I can not get the terminal open. The only keys that seems to work is Ctrl+left/right arrow. Mouse pointed move but right click is also does not work. I think it needs another treatment. Gagea

---

### Post by drs305 on 2010-10-06
Have you tried booting another kernel or the recovery mode? If available, you should have these choices in your Grub2 boot menu. 

If you don't see the boot menu, hold down the SHIFT key during the first part of the boot and it should display.

If you can't change the way it boots, use a LiveCD and boot to the Desktop. Open a terminal (ALT-F2 should work in the LiveCD) or Applications, Accessories, Terminal.

Mount your real Ubuntu terminal (change **XY** as necessary:
```
sudo mount /dev/sd**XY** /mnt  # Example:  sudo mount /dev/sd**a5** /mnt
gksu nautilus /mnt/home/<yourusername>/
```

---

### Post by gagea on 2010-10-06
> **drs305 said:**
> Have you tried booting another kernel or the recovery mode? If available, you should have these choices in your Grub2 boot menu. 

If you don't see the boot menu, hold down the SHIFT key during the first part of the boot and it should display.

If you can't change the way it boots, use a LiveCD and boot to the Desktop. Open a terminal (ALT-F2 should work in the LiveCD) or Applications, Accessories, Terminal.

Mount your real Ubuntu terminal (change **XY** as necessary:
```
sudo mount /dev/sd**XY** /mnt  # Example:  sudo mount /dev/sd**a5** /mnt
gksu nautilus /mnt/home/<yourusername>/
```

Thanks. I used the ubuntu on external usb memory stick. There is no recovery mode available in boot. 

I am now using ubuntu on another usb stick. I wonder how If I can use it to mount it. How can I find which device it is? 

Sprry if questions are too simple.
Gagea

---

### Post by gagea on 2010-10-06
[QUOTE=gagea;9933213]Thanks. I used the ubuntu on external usb memory stick. There is no recovery mode available in boot. 

I am now using ubuntu on another usb stick. I wonder how If I can use it to mount it. How can I find which device it is? 

this is the message:

ubuntu@ubuntu:/$ sudo mount /dev/sdd/mnt
mount: can't find /dev/sdd/mnt in /etc/fstab or /etc/mtab
ubuntu@ubuntu:/$ 


Sorry if questions are too simple.
Gagea

---

### Post by drs305 on 2010-10-06
> **gagea said:**
> Thanks. I used the ubuntu on external usb memory stick. There is no recovery mode available in boot. 

I am now using ubuntu on another usb stick. I wonder how If I can use it to mount it. How can I find which device it is? 

Sprry if questions are too simple.
Gagea

1. If you can get to the Grub menu, to boot in recovery mode you can highlight the Ubuntu menu entry, press "e" to open the entry for editing. 

Find the "linux" line. At the end is probably "quiet splash".
Remove those entries and add "single" as the last entry on the linux line.

Press CTRL-x to boot and it should start in recovery mode.

2. From the LiveCD Desktop, probably the most familiar way for you to view the drive is to open Disk Utility. System, Administration, Disk Utility.

See if you can recognize your Ubuntu partition. If you click on a partition, look in the middle right just below the graphic and you can see the "Device" (sda1, sda5, etc).

3. Do you know if you had more than one kernel? Once you have the correct partition mounted, you can look in the /mnt/boot partition (if you mount it as I said earlier) to see if you have different kernels (for instance a vmlinuz-2.6.32-24 and a vmlinuz-2.6.32.25). If you do have an older one, you could try to use it via the same editing of the Grub menu as I talked about in #1. You would just have to change the number in the "linux" and "initrd" lines to the lower number (for instance, change -25 to -24).

---

### Post by gagea on 2010-10-06
> **drs305 said:**
> 1. If you can get to the Grub menu, to boot in recovery mode you can highlight the Ubuntu menu entry, press "e" to open the entry for editing. 

Find the "linux" line. At the end is probably "quiet splash".
Remove those entries and add "single" as the last entry on the linux line.

Press CTRL-x to boot and it should start in recovery mode.

2. From the LiveCD Desktop, probably the most familiar way for you to view the drive is to open Disk Utility. System, Administration, Disk Utility.

See if you can recognize your Ubuntu partition. If you click on a partition, look in the middle right just below the graphic and you can see the "Device" (sda1, sda5, etc).

3. Do you know if you had more than one kernel? Once you have the correct partition mounted, you can look in the /mnt/boot partition (if you mount it as I said earlier) to see if you have different kernels (for instance a vmlinuz-2.6.32-24 and a vmlinuz-2.6.32.25). If you do have an older one, you could try to use it via the same editing of the Grub menu as I talked about in #1. You would just have to change the number in the "linux" and "initrd" lines to the lower number (for instance, change -25 to -24).


Thanks. I found that my usb disc is sdd1. But 

sudo mount  dev/sdd1/mnt 

give following error: 
ubuntu@ubuntu:/$ sudo mount  dev/sdd1/mnt 
mount: can't find dev/sdd1/mnt in /etc/fstab or /etc/mtab
ubuntu@ubuntu:/$ 
.

I am sorry I do not know what is Grub menu. When I turn on computer, it is Toshiba laptop, press F12, and then the page in attached image come up. 
I really need to recover my data. I have a meeting with my supervisors tomorrow. 

Please give me simple way. 

Thanks.

---

### Post by drs305 on 2010-10-06
> **gagea said:**
> Thanks. I found that my usb disc is sdd1. But 

sudo mount  dev/sdd1/mnt 

give following error: 
ubuntu@ubuntu:/$ sudo mount  [COLOR="Red"]dev/[/COLOR]sdd1/mnt 
mount: can't find dev/sdd1/mnt in /etc/fstab or /etc/mtab
ubuntu@ubuntu:/$ 
.

I am sorry I do not know what is Grub menu. When I turn on computer, it is Toshiba laptop, press F12, and then the page in attached image come up. 
I really need to recover my data. I have a meeting with my supervisors tomorrow. 

Please give me simple way. 

Thanks.

Just so I understand: sdd1 is your Ubuntu installation - you installed and were running Ubuntu on sdd1?

From the picture you posted, just select (press ENTER) the first entry to boot you to the Ubuntu Desktop. Then, when you are on the Desktop, you want to mount your Ubuntu partition. 

If it is, you forgot a "[COLOR="Red"]/[/COLOR]", and don't forget the [COLOR="Red"]1[/COLOR]. The command would be:
```
sudo mount **[COLOR="Red"]/[/COLOR]**dev/sdd[COLOR="Red"]1[/COLOR] /mnt
```

Once you mount it, you should find your files on /mnt
We haven't tried to fix it. For now, we are just trying to allow you to see and copy your important files from your Ubuntu installation.

From the LiveCD Desktop, please go to the following site, download the boot info script and post the contents of RESULTS.txt here.  How to run the script is posted on the web site:
[http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")
It may help us figure out why your computer won't boot Ubuntu.

---

### Post by gagea on 2010-10-06
> **drs305 said:**
> From the picture you posted, just select (press ENTER) the first entry to boot you to the Ubuntu Desktop. Then, when you are on the Desktop, you want to find your Ubuntu partition. Is Ubuntu installed on your usb drive?

If it is, you forgot a "[COLOR=Red]/[/COLOR]", and don't forget the [COLOR=Red]1[/COLOR]. The command would be:
```
sudo mount **[COLOR=Red]/[/COLOR]**dev/sdd[COLOR=Red]1[/COLOR] /mnt
```Once you mount it, you should find your files on /mnt
We haven't tried to fix it. For now, we are just trying to allow you to see and copy your important files from your Ubuntu installation.


Look, the broken ubuntu installed on usb drive. As I mentioned before, I select the first option from the jpeg in previous e-mail to go to Ubuntu Desktop. But, it is only desktop without any of menu bars (none of Application, Places, System, .. is shown up). The desktop is completly empty and only shows the background. None of the key work. I can not open a terminal. 

So, I am on another ubuntu that also installed on usb drive. The following lines are the result of executing 
sudo mount **[COLOR=Red]/[/COLOR]**dev/sdd[COLOR=Red]1[/COLOR] /mnt 

ubuntu@ubuntu:~$ sudo mount /dev/sdd1 /mnt
ubuntu@ubuntu:~$ gksu nautilus /mnt/home/ubuntu/
(nautilus:5819): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
Initializing nautilus-gdu extension

** (nautilus:5819): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:5819): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:5819): WARNING **: No marshaller for signature of signal 'ShareCreateError'
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


--- Hash table keys for warning below:
--> inode/directory
--> root
--> l16
Shutting down nautilus-gdu extension

(nautilus:5819): Eel-WARNING **: "unique eel_ref_str" hash table still has 3 elements at quit time (keys above)

(nautilus:5819): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 3 elements at quit time
ubuntu@ubuntu:~$ ^C
ubuntu@ubuntu:~$ 


Now when I open the usb content, the attached image is the folders, etc. 

Please tell me where are my Documents data?

Thanks

Gagea

---

### Post by drs305 on 2010-10-06
Summary:

The Ubuntu you want to boot to DOES boot to the Desktop but there are no icons.

You have another Ubuntu on the same drive that you CAN boot to the Desktop.

Correct?

The folders you are showing me are the files on an installation disk, not your actual Ubuntu installation.

Run the boot info script and post the results and maybe we can understand your situation.

---

### Post by gagea on 2010-10-06
[QUOTE=drs305;9933369]Summary:

The Ubuntu you want to boot to DOES boot to the Desktop but there are no icons 

[COLOR=Red]Yes. when I boot it, there are no icons on the desktop. Keyborad also does not work.[/COLOR]

You have another Ubuntu on the same drive that you CAN boot to the Desktop.
Correct?

[COLOR=Red]No I do not have another ubuntu on the usb that its ubuntu is broken. I am on another usb-ubuntu at the moment. What I showed you is that I connect the usb contain broken ubuntu to the computer and it contents are as I mentioned in previous message (image).  
[/COLOR]


The folders you are showing me are the files on an installation disk, not your actual Ubuntu installation.

Run the boot info script and post the results and maybe we can understand your situation.

[COLOR=Red]What do you mean by this?[/COLOR]

Sorry I am beginner in ubuntu since March.

---

### Post by drs305 on 2010-10-06
From a previous post:

From the LiveCD Desktop, please go to the following site, download the boot info script and post the contents of RESULTS.txt here. How to run the script is posted on the web site:

[http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")

It may help us figure out why your computer won't boot Ubuntu. Make sure the broken Ubuntu is connected when you run the script.

---

### Post by gagea on 2010-10-06
> **drs305 said:**
> From a previous post:

From the LiveCD Desktop, please go to the following site, download the boot info script and post the contents of RESULTS.txt here. How to run the script is posted on the web site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

It may help us figure out why your computer won't boot Ubuntu. Make sure the broken Ubuntu is connected when you run the script.


Hello friend,

I am really sorry to bother you. the data enclosed. 

Gagea

---

### Post by Quackers on 2010-10-06
Gagea if you need to post the output of a text file go to New Reply and write your message then paste the contents of the file using the # sign in the top bar of the reply window. It then appears like this (your boot info script)

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb
 => Syslinux is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /BOOT/BCD

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb2 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb2 starts at sector 206097885.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdd1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdd1 starts at sector 62.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2edfc607

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048     3,074,047     3,072,000  27 Hidden HPFS/NTFS
/dev/sda2    *      3,074,048   456,753,151   453,679,104   7 HPFS/NTFS
/dev/sda3         456,753,152   472,678,399    15,925,248   7 HPFS/NTFS
/dev/sda4         472,678,400   488,396,799    15,718,400  17 Hidden HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000bd19a

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   206,097,884   206,097,822   b W95 FAT32
/dev/sdb2         206,097,885   488,392,064   282,294,180   b W95 FAT32


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 8103 MB, 8103395328 bytes
250 heads, 62 sectors/track, 1021 cylinders, total 15826944 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0006f9c1

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *             62    15,825,499    15,825,438   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       d92cc88b-1e06-4906-bd64-0fb7e92164af   ext3                                     
/dev/sda1        B4D07DABD07D7488                       ntfs       TOSHIBA SYSTEM VOLUME         
/dev/sda2        4E8C81B28C81955D                       ntfs       S3A6747D002                   
/dev/sda3        AC649CA0649C6EB8                       ntfs                                     
/dev/sda4        2000DA9300DA6F72                       ntfs       HDDRECOVERY                   
/dev/sdb1        65E3-E824                              vfat       UBUNTU                        
/dev/sdb2        67EA-BAA6                              vfat       DATA                          
/dev/sdd1        FEED-C4DF                              vfat       UBUNTU                        

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sdb2        /media/DATA              vfat       (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sdd1        /media/UBUNTU            vfat       (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sdd1        /mnt                     vfat       (rw)

=======Devices which don't seem to have a corresponding hard drive==============

sdc 
```

---

### Post by drs305 on 2010-10-06
Thank you for posting the results. From the output, there are no partitions currently formatted for a linux filesystem. This means that Ubuntu is not currently installed from what the boot info script can see.

You do have two drives (probably your thumb drives) that are labeled UBUNTU but both are formatted to vfat (and have vfat-type UUIDs).

The script did find an "sdc" but can't get any information about it.

Or perhaps I am just misunderstanding you and you WANT to install Ubuntu but can't because the disk doesn't allow you to see the Desktop menus...?

The good news is that you should still be able to boot into your Windows installation as long as the BIOS boots to your sda (Windows) drive first.

---

### Post by gagea on 2010-10-06
```

#
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb
 => Syslinux is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /BOOT/BCD

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb2 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb2 starts at sector 206097885.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdd1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdd1 starts at sector 62.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2edfc607

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048     3,074,047     3,072,000  27 Hidden HPFS/NTFS
/dev/sda2    *      3,074,048   456,753,151   453,679,104   7 HPFS/NTFS
/dev/sda3         456,753,152   472,678,399    15,925,248   7 HPFS/NTFS
/dev/sda4         472,678,400   488,396,799    15,718,400  17 Hidden HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000bd19a

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   206,097,884   206,097,822   b W95 FAT32
/dev/sdb2         206,097,885   488,392,064   282,294,180   b W95 FAT32


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 8103 MB, 8103395328 bytes
250 heads, 62 sectors/track, 1021 cylinders, total 15826944 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0006f9c1

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *             62    15,825,499    15,825,438   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       d92cc88b-1e06-4906-bd64-0fb7e92164af   ext3                                     
/dev/sda1        B4D07DABD07D7488                       ntfs       TOSHIBA SYSTEM VOLUME         
/dev/sda2        4E8C81B28C81955D                       ntfs       S3A6747D002                   
/dev/sda3        AC649CA0649C6EB8                       ntfs                                     
/dev/sda4        2000DA9300DA6F72                       ntfs       HDDRECOVERY                   
/dev/sdb1        65E3-E824                              vfat       UBUNTU                        
/dev/sdb2        67EA-BAA6                              vfat       DATA                          
/dev/sdd1        FEED-C4DF                              vfat       UBUNTU                        

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sdb2        /media/DATA              vfat       (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sdd1        /media/UBUNTU            vfat       (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sdd1        /mnt                     vfat       (rw)

=======Devices which don't seem to have a corresponding hard drive==============

sdc

```

---

### Post by gagea on 2010-10-06
> **gagea said:**
> Hello friend,

I am really sorry to bother you. the data enclosed. 

Gagea


I posted the result, Bot nobody can tell me what is the problem. Could some body tell me how to get my data retrieved.

---

### Post by drs305 on 2010-10-06
> **gagea said:**
> I posted the result, Bot nobody can tell me what is the problem. Could some body tell me how to get my data retrieved.

We posted at about the same time. You may not have seen my Post #16.

---

### Post by gagea on 2010-10-06
> **drs305 said:**
> Thank you for posting the results. From the output, there are no partitions currently formatted for a linux filesystem. This means that Ubuntu is not currently installed from what the boot info script can see.

You do have two drives (probably your thumb drives) that are labeled UBUNTU but both are formatted to vfat (and have vfat-type UUIDs).

The script did find an "sdc" but can't get any information about it.

Or perhaps I am just misunderstanding you and you WANT to install Ubuntu but can't because the disk doesn't allow you to see the Desktop menus...?

The good news is that you should still be able to boot into your Windows installation as long as the BIOS boots to your sda (Windows) drive first.

Thanks a lot. Sorry I did not see this message. 

/dev/sdd1        FEED-C4DF                              vfat       UBUNTU   
This device is the one that the broken ubuntu is on it. I think I can not still explain what is problem. I can start the ubuntu on the above device. But the menu bar, etc is not there. There is only a glass desktop with desktop background. No any icon. The question is how to get my data from "ubuntu/Documents ". Thanks.

---

### Post by drs305 on 2010-10-06
It could be that the Ubuntu usb files have some errors. I have not used a USB to install or boot Ubuntu.

However, the files in /UBUNTU/Documents according to the boot info script are not formatted to ext2, ext3 or ext4. The script shows all your partitions are either vfat or NTFS. You should be able to read and perform actions on them using Windows.

To get back to your original post, I don't know why the installation will not properly display the Desktop once you boot. It could be a problem with the installation files. You could try to download them again. Or perhaps try Xubuntu, a lighter version of Ubuntu that may work better on your computer.

I am about to sign off for the night. I will check back tomorrow. Best of luck.

---

### Post by gagea on 2010-10-06
> **drs305 said:**
> It could be that the Ubuntu usb files have some errors. I have not used a USB to install or boot Ubuntu.

However, the files in /UBUNTU/Documents according to the boot info script are not formatted to ext2, ext3 or ext4. The script shows all your partitions are either vfat or NTFS. You should be able to read and perform actions on them using Windows.

To get back to your original post, I don't know why the installation will not properly display the Desktop once you boot. It could be a problem with the installation files. You could try to download them again. Or perhaps try Xubuntu, a lighter version of Ubuntu that may work better on your computer.

I am about to sign off for the night. I will check back tomorrow. Best of luck.


Thanks. I tried to open the usb data in windows vista, But all I could see was what I can see on ubuntu. Anyway, have a good night. 

Gagea

:-(

---

