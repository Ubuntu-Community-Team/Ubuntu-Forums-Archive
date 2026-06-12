---
title: "Cannot Boot Windows after Ubuntu Removal!"
date: 2010-06-30
forum: General Help
---

### Post by jackmac on 2010-06-30
Hi,
Today I installed openSUSE and then it's boot interface took over my GRUB boot interface. It also did not give me the ability to boot Ubuntu and came up with an error when trying to boot windows 7. So I deleted the openSUSE partion through the Disk Utility tool in Ubuntu (I used a LiveCD to do this) and then decided that I didn't really need Ubuntu any more, so I deleted that the same way aswell.

Now when I start my computer, I am greeted with the following message: No Boot device available - Strike F1 to retry boot, F2 for setup utility and F5 for Diagnostics. I am pretty sure this is a DELL error as I have a Dell Inspiron 1545. I then inserted my Windows 7 installation disk and followed the prompts, then clicked repair my computer. It came with two options, on asking me to select my operating system from the list and the other asking for a system restore file. From other threads people have been told to go into the first option. My operating system (Windows 7) was not detected but I proceded anyway. At the next screen I clicked command prompt and typed the following as per instructions in other threads
```
bootrec.exe/fixmbr
```This Worked and displayed the message: Windows has completed the operation sucessfully
Next, As per instructions I typed
```
bootrec.exe/fixboot
```And to my dismay this message showed up: Element Not Found

I explored the other commands in the bootrec.exe function and found the command
```
bootrec.exe/scanos
```It searched for Windows installation files and actually found them in the D:/ drive. I discovered that when openSUSE was installed or Ubuntu or openSUSE was deleted, it changed my Windows and my Work Files, Games, Work etc. drive from C:/ to D:/

I then tried the command
```
bootrec.exe/rebuildbcd
```It searched for the Windows Instillation Files and once again found them in D:/
It then asked if I wanted to add these files to the boot menu Yes (Y) No (N) or All (A)
I typed Y for Yes and it popped up with the error element not found. I also tried Yes but came out with the same error. 

I am now totally unable to access my Windows and can only boot Ubuntu from a live CD.
Any help would be greatly appreciated! :p

---

### Post by wilee-nilee on 2010-06-30
Post the boot script in my signature in code tags as described.

---

### Post by jackmac on 2010-06-30
> **wilee-nilee said:**
> Post the boot script in my signature in code tags as described.
Below is the RESULTS.TXT output as requested

             ```
  Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda3 starts 
                       at sector 30801920. But according to the info from 
                       fdisk, sda3 starts at sector 30796605. According to 
                       the info in the boot sector, sda3 has 883048495 
                       sectors, but according to the info from fdisk, it has 
                       883060919 sectors.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        80,324        80,262   6 FAT16
/dev/sda3    *     30,796,605   913,857,524   883,060,920   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        3030-3030                              vfat       DellUtility                   
/dev/sda3        9414ABD814ABBB9C                       ntfs       Hardrive - Jack               
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

=======Devices which don't seem to have a corresponding hard drive==============

sdb 
```

---

### Post by wilee-nilee on 2010-06-30
Just hang a bit there is another user on line that will probably have some answers for you.

---

### Post by jackmac on 2010-06-30
> **wilee-nilee said:**
> Just hang a bit there is another user on line that will probably have some answers for you.

Ok, Thanks heaps for your assistance so far! :p

---

### Post by oldfred on 2010-06-30
You do not have any Ubuntu or openSuse shown. Is a drive missing?

Your windows is missing its boot partition that had these: It probably was sda2 and might be recoverable with testdisk.
/bootmgr /Boot/BCD

Your running of the windows repairs on sda3 with the boot flag should have repaired sda3 and made it bootable. 

But the script is showing some issue with your sda3 partition.

I have not run testdisk but many have and been able to fix many things:
enable the "universe" repository to download testdisk
System>Administration>Software Sources>Ubuntu Software.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

---

### Post by jackmac on 2010-07-01
Sorry, I'm a bit of a N00B with these things. How do I install the repo? In the Ubuntu Software section what do I do? It is downloading from Main Server and Lucid Lynx is installable from my LiveCD. What do i do? :confused:

---

### Post by cr4321 on 2010-07-01
Use Gparted from the live cd and change your D-drive flag to "boot". (make the drive active) and then try. You may have to redo the Fixmbr and Fixboot once again.

cr4321

---

### Post by wilee-nilee on 2010-07-01
> **cr4321 said:**
> Use Gparted from the live cd and change your D-drive flag to "boot". (make the drive active) and then try. You may have to redo the Fixmbr and Fixboot once again.

cr4321

The D drive is set to boot.

Thread starter oldfreds advice is sound, it just may take some time to get you orientated as to what to do, and how to do it.

If you have a external HD or a way to save anything that is in the MS setup I would boot a Live Ubuntu cd and back it up just in case a reinstall has to be done in the end.

---

### Post by jackmac on 2010-07-01
Hi,
I currently have TestDisk running, after it is finished I will hopefully get back to you with some good news!
Thanks
    ~Jack Mac :guitar:

---

### Post by jackmac on 2010-07-01
Ok,
I have ran TestDisk and now when I boot my computer from the Internal HardDrive I encounter the System Diagnostics Menu! Anyone have a where to from here for me?

---

### Post by jackmac on 2010-07-01
Hi Again,
I just booted Ubuntu via. the LiveDisk and entered The Disk Utility. Attached is a screenshot of what I saw
I then entered GParted and I saw something enterily different! (See Attached)
I don't know what to do! I am pulling my hair out!
Thankyou for any help you may be able to offer
~Jack Mac

---

### Post by oldfred on 2010-07-01
We seem to see that gparted does not always show NTFS drives when you have issues in the drive. I had that problem with my XP partition and after running chkdsk gparted then worked. the partition is still there and disk utility sees it.

I would run chkdsk until you do not get any errors and try running the windows fixes on your c: or d: which ever it is.

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk or repair disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands:
BootRec.exe /fixmbr   #updates MBR master boot record  do not run if you still want grub
chkdsk C: /r /f (may have to run /r or /f as separate entries) rerun until no errors
BootRec.exe /FixBoot  #updates PBR partition boot sector
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd

How to fix Vista/Window 7 when the boot files are missing - rebuild BCD with bcdedit
[http://ubuntuforums.org/showpost.php?p=5726832&postcount=4](http://ubuntuforums.org/showpost.php?p=5726832&postcount=4)

---

### Post by jackmac on 2010-07-02
> **oldfred said:**
> 
chkdsk C: /r /f (may have to run /r or /f as separate entries) rerun until no errors


Hi,
Thanks for your reply! I was just wondering if the chkdsk command had to be used on the C:/ drive. Could it be used on the D:/drive where my Windows System Files have been moved to and are now held?

Thanks in Advance,
~Jack Mac

---

### Post by oldfred on 2010-07-02
You should run chkdsk on all NTFS partitions on a regular basis. Whatever windows calls them. If you do not specify a "drive" is runs on the current drive or you can specify c:, d: e: or whatever. You also have to rerun it until you get no errors.

Vista/7 CHKDSK
chkdsk C: /f /r
/f : Fixes errors on the disk.
/r : Locates bad sectors and recovers readable information.
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

---

### Post by jackmac on 2010-07-02
When I run the chkdsk command on my D: drive, I do not seem to get any errors, only the error about being unable to transfer sommething with the status of 50. I ran the chkdsk command twice and got the same message. When I run bootrec.exe/fixboot I get the error that I need to make sure the drive is not corrupted etc... Would it help if I deselected the Windows 7 thing when it asks me what operating system to choose?

Thanks in Advance,
~Jack Mac

---

### Post by oldfred on 2010-07-02
I am running out of suggestions. I do not know if this is related to your problem or not:

If Microsoft's Checkdisk (chkdsk) failed to repair the MFT, run TestDisk, also rebuild boot sector
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)

---

### Post by jackmac on 2010-07-06
Hi,

Sorry I haven't been able to get on latley, there was a problem with my ISP. I was wondering if a full windows re-install would fix the problem? And if so how can I put all my programs back on the computer without the need to reinstall them?

Thanks,
~Jack Mac

---

