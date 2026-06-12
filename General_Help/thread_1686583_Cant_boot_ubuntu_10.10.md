---
title: "Cant boot ubuntu 10.10"
date: 2011-02-12
forum: General Help
---

### Post by himanshu124 on 2011-02-12
i installed ubuntu a fews days back. it was working fine till now. but today my desktop crashed due to power failure. When i again started the machine and tried to boot Ubuntu i m  getting the following message in command screen:-

"Minimal BASH-Like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists is possible device & file completions."

Please tell me what to do.

---

### Post by Rubi1200 on 2011-02-12
Hi and welcome to the forums :-)

How did you install Ubuntu; regular or Wubi?

What other operating systems do you have?

Please do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by himanshu124 on 2011-02-16
hey rubi thanx a lot for ur help.
i had done a Wubi installation of Ubuntu 10.04 LTS and then upgraded it to 10.10
i m currently having Windows XP installed on my system other than ubuntu,

Here are the contents of RESULTS.txt file...


```
                
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
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
    Operating System:  Windows XP
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr /wubildr

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    39,102,209    39,102,147   c W95 FAT32 (LBA)
/dev/sda2          39,102,210    78,156,224    39,054,015   f W95 Ext d (LBA)
/dev/sda5          39,102,273    78,156,224    39,053,952   b W95 FAT32


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    79,976,672    79,976,610   c W95 FAT32 (LBA)
/dev/sdb2          79,976,673   312,576,704   232,600,032   f W95 Ext d (LBA)
/dev/sdb5          79,976,736   312,576,704   232,599,969   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        B405-2B83                              vfat       PHOTOS                        
/dev/sda2: PTTYPE="dos" 
/dev/sda5        3C1B-4087                              vfat                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        FA8F-8E47                              vfat       SOFTWARES                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        C29022C79022C231                       ntfs       Movies and Videos             
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
C:\wubildr.mbr="Ubuntu"  

================================ sdb1/boot.ini: ================================

[boot loader] 
timeout=3 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
C:\="Unidentified operating system on drive C."  
C:\wubildr.mbr = "Ubuntu"

```


Now please tell me what to do next.

---

### Post by Rubi1200 on 2011-02-16
Thanks for posting the results.

There are some things I am not clear about and ask if you could explain please.

1. are you able to boot Windows normally?

2. you seem to be missing essential files from the Wubi install; do you know what happened?

For example, the Wubi partition should look like this:
```
Boot files/dirs:   /Windows/System32/winload.exe /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk
```
Ignore the fact that this was taken from another version of Windows. Take a look at your results and you will see what I mean about missing files.

Did you run chkdsk in Windows?

If you can boot Windows, try finding the files. They might be in a hidden folder called something like C:\Found.000

---

### Post by himanshu124 on 2011-02-16
Windows is booting perfectly normal.

Actually my system crashed due to power failure. At that time i was using Ubuntu.
After the power was restored i tried to boot Ubuntu but i was getting the above mentioned error.

I haven't used chkdsk.

Regarding the "Found.000" folders. I have mistakenly deleted them.
I thought there were some kind of malware programs in them. :(

Now what can be done?

---

### Post by Rubi1200 on 2011-02-16
Hi again himanshu124,
after consulting with bcbc, a long-standing forum member and expert on Wubi installs, the bad news is that unfortunately your Wubi install is probably unrecoverable.

You could try and use an undelete utility for Windows to try and get those C:\Found.000 folders back. It is a long shot though. And, even it it works, the root.disk (which may or may not be there) could be in such a bad state as to make it unusable anyway.

The best thing, in my opinion, would be to do a fresh install of Wubi again.

See here for more details:
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

Take notice of the warning about updating grub packages please.

Sorry I do not have better news to tell you.

---

### Post by himanshu124 on 2011-02-16
Hi Rubi 
Thanks for your help.
i appreciate your efforts.

K then as there is no other way out than to do a reinstallation, i would go ahead with that
and from next time onwards would be more careful while deleting unwanted files.

Regards,
Himanshu.

---

### Post by Rubi1200 on 2011-02-17
No problem, you are more than welcome :-)

In future, if something goes wrong with a Wubi install, first check either the [Wubi Guide]("https://wiki.ubuntu.com/WubiGuide") or [Wubi Megathread]("http://ubuntuforums.org/showthread.php?t=1639198") for answers.

If that doesn't help, then start a new thread and ask here on the forum.

Good luck with everything.

---

