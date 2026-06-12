---
title: "mountint ntfs drive using ubuntu on a usb"
date: 2010-08-12
forum: General Help
---

### Post by cyke1 on 2010-08-12
Hey guys I'm a noob using Ubuntu, so please bear  with me.  My netbook running xp recently stopped booting up,  I just get  some weird error that needs a reinstall,  but before I do a that I want  to get some pics that I only have on the netbook.   I'm using the  netbook version of ubuntu running off a usb.  I have tried following the  numerous tutorials online but I can't get it too mount.  When I try  using Gparted it shows up, but it won't do anything with the drive and the unmount option is grayed out.  I've tried downloading and installing NTFS  configuration tool but I keep getting an error when I try to run it,I downloaded it a few time already.   The NTFS drive shows up in the disk utility and it says it's good.  I've been trying to do this for almost 2 days now.  Is there anything I  can do to get this to mount so I can hopefully get my pics.   Thanks for  any help.

---

### Post by bobcollard on 2010-08-12
you probably need ntfs-3g as well as ntfs-config, check Synaptic Package Manager, search ntfs.

---

### Post by cyke1 on 2010-08-12
Thanks I just did that but most were preinstalled and only 3 items under NTFS were not checked. Installed them anyway but same result. BTW I just noticed in Gparted the drive is 149.05GiB but in disk utility it is 160GB  could this be causing the problem.

---

### Post by oldfred on 2010-08-12
Gparted & Ubuntu do not like to mount a NTFS partition that needs chkdsk run. It may damage the journal as chkdsk will use the journal to recover the error.

If you have a XP usb flash drive run chkdsk from that.

While you cannot use a Vista or 7 repair disk to repair XP you can use it to run chkdsk.

I downloaded this, copied to a CD as I had no win7 to use the windows command to copy to a USB and from CD copied to a USB. Windows has tools to copy an ISO to a USB.

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista will not repair XP (they create the boot sectors differently) but can run chkdsk.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)


Vista/7 CHKDSK
chkdsk C: /f /r
/f : Fixes errors on the disk.
/r : Locates bad sectors and recovers readable information.
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)


You may be able to run some fixes from testdisk:
If Microsoft's Checkdisk (chkdsk) failed to repair the MFT, run TestDisk, also rebuild boot sector
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)

---

### Post by cyke1 on 2010-08-12
Thanks, sorry I didn't mention it I have XP on a usb that is bootable,  but when I try that I can the blue screen and I think the error 71, and it tells me to press f8 on boot up but nothing happens when I do that.  Also the netbook is a acer aspire one.

---

### Post by cyke1 on 2010-08-14
I think I'm making some progress with this, I borrowed a friends  recovery disk for the same type of netbook.  Now after booting with the  usb I get Please select OS to start and a bunch of choice:  
1st text mode setup
2nd GUI mode setup, continue setup + 1st start windows
---> DEBUB, in case of HAL.DLL or NTOSKRNL.EXE not found errors <---
Debug boot rDisk 1 partition 2
Debug boot rDisk 1 partition 3
Debug boot rDisk 1 partition 4
Debug boot rDisk 2 partition 1
Debug boot rDisk 2 partition 2
Debug boot rDisk 2 partition 3
Debug boot rDisk 2 partition 4


when I chose the 1st choice i get the install windows thing but it only sees the usb
when I choose the 2nd I get Windows could not start because the  following file is missing or corrupt <Windows  root>\system32\hal.dll.
Please re-install a copy of the above file.
I don't know how to do this.

I tried  all the options I get with the xp recovery usb,    now when I get to the repair I get a MS XP recovery console I'm lost  it's dos and I have tried the chkdsk and bootcfg,  but both are giving  me errors 

C:\>chkdsk c: 
The specified drive is not valid, or there is no disk in the drive

C:\>bootcfg /scan
Scanning all disks for Windows installations.
Please wait, since this may take a while...
Error: Failed to successfully scan disks for Windows installations.
This error may be caused by a corrupt file system, which would prevent  bootcfg from sucessfully scanning. Use chkdsk to detect any errors .

Note: This operation must complete sucessflly in order for the /add or rebuild commands to be utilized.

I really don't know what to do please help.  Thanks

---

### Post by oldfred on 2010-08-14
Fix WinXP hal.dll Post #8
[http://ubuntuforums.org/showthread.php?t=1410696](http://ubuntuforums.org/showthread.php?t=1410696)
From Recovery Console run bootcfg /rebuild (fixes boot.ini which often causes hal.dll errors) and CHKDSK /r (which checks the drive for errors and fixes any).

Missing hal.dll not always missing, but other errors or boot.ini wrong partition
[http://members.iinet.net.au/~herman546/p15.html#hal.dll_is_missing_or_corrupt](http://members.iinet.net.au/~herman546/p15.html#hal.dll_is_missing_or_corrupt)
[http://pcsupport.about.com/od/findbyerrormessage/a/missinghaldll.htm](http://pcsupport.about.com/od/findbyerrormessage/a/missinghaldll.htm)
Error message: "Windows could not start because of a computer disk hardware configuration problem"
[http://support.microsoft.com/kb/314477](http://support.microsoft.com/kb/314477)
[http://michaelstevenstech.com/XPrepairinstall.htm](http://michaelstevenstech.com/XPrepairinstall.htm)

---

### Post by cyke1 on 2010-08-14
Thanks Oldfred but none of those options would seem to fit for me since I can't do anything with bootcfg.  I have noticed that since I changed the boot order,  the windows recovery usb cannot see the main HD only the usb.  But when I boot with Ubuntu the disk utility see it and so does gparted,  also when I tried using a Windows 7 usb I see 2 drives the C drive which I can't access and an X drive which I think is the recovery partition.  But I don't know what to do with that info.   Do you think if tried to install windows 7 that from there I could access my other windows files.  Thanks again.

---

### Post by oldfred on 2010-08-15
From Ubuntu you can force mount. It may damage whatever file(s) that windows chkdsk would repair. But if just reading it may be ok.
[http://mpathirage.com/how-to-fix-ntfs-mount-error-on-ubuntu/](http://mpathirage.com/how-to-fix-ntfs-mount-error-on-ubuntu/)

You can also try testdisk as it may repair some related things:
If Microsoft's Checkdisk (chkdsk) failed to repair the MFT, run TestDisk, also rebuild boot sector
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)
If anyone has an NTFS drive showing up as RAW, use Windows Active Partition Recovery. Just right click on your partition and select "Fix Boot Sector"
Windows repairs general malware/duplicate scanners etc:
[http://forums.majorgeeks.com/showthread.php?t=35407](http://forums.majorgeeks.com/showthread.php?t=35407)

---

### Post by cyke1 on 2010-08-16
I will try testdisk again later cause right now I'm running the update managet in ubuntu and it keeps stalling on the grub install telling me it can't install on the main drive and the usb that ubuntu is running off of,  it is a 8gb usb and I did 3gb persistance.  Should I be worried about this?  Also before I did the update I tried testdisk and I was getting no drive error,  so I'm getting a little worried.  Thanks

---

### Post by cyke1 on 2010-08-16
Hey guys a little more help hope this will solve my problems.  After running testdisk again after the update it wouldn't install saying something about universe.  Not sure what to do with that I found a tutorial using ntfsfix, it tells me to sudo fdisk-l to get a list of drives.  This is what I get 

Disk /dev/sda: 160.0 B, 160041885696 bytes
255 heads, 63 sectors/tracks,19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
Disk identifier: 0x2052474d

This doesn't look like a partition table
Probably you selected the wrong device.

     Device Boot          Start          End         Blocks      Id   System
/dev/sda1 ?                  410    119791   958924038+   12   Compaq diagnostics
Partition 1 does not end on cylinder boundary.
/dev/sda2  ?            121585   234786    909287957+  43   Unknown
Partition 2 does not end on cylinder boundary.
/dev/sda3 ?              14052     14052                 5      72   Unknown
Partition 3 does not end on cylinder boundary.
/dev/sda4               164483   164486             25945    0    Empty
Partition 4 does not end on cylinder boundary.


Partition table entries are not in disk order

Disk /dev/sdb: 8036 MB, 8036285952 bytes
255 heads, 63 sectors/tracks, 977 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 51bytes / 512 bytes
Disk identifier: 0x323ddf79

/dev/sdb1  *             1          978   7847904          b  W95 FAT32
Partition 1 has different physical/logical endings"
   phys=(976,254,63) logical=(977,5,51)

I don't know what to do with this info, so I can mount the ntfs drive.  Thanks again

---

### Post by oldfred on 2010-08-16
If it says you have to enable universe then enable universe. It may not be enabled automatically on the liveCD. Look in Software Sources under administration.

repairs including testdisk info & link to testdisk, testdisk is in repository and on most repairCDs
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
download TestDisk [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
As described, it has an option to "Recover NTFS boot sector from its backup"
Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by cyke1 on 2010-08-17
Thanks OldFred this info has been a great help,  I'm running photorec for the 2nd time today, but I only have a 8gb thumb drive and it doesn't have enough space for all the pics on the NTFS drive I plugged in an external HD but I don't know how to change where photorec saves the found files.  Also is there a similar program that will allow me to get avi files,  cause the camera we have saves the videos in avi?   Thanks again.

---

### Post by cyke1 on 2010-08-18
Thanks again OldFred, after doing some reading I was able to rerun testdisk and get the files I needed but after rebooting I can no longer see the partition and it won't boot into windows.  BTW I plan on doing a clean install of windows,  should I put ubuntu on 1st or windows.  Thanks

---

### Post by oldfred on 2010-08-18
The only real requirement is that windows has to be in a primary partition. Linux can be in the logical partitions inside the extended partition. That said if you are doing a total reinstall putting windows first is slightly easier. Windows will not 'see' any linux partitions so you have to have either free space or NTFS partitions set up for it. 

Also installing windows first lets windows install its boot loader first and then grub can overwrite it. If windows is second you do have to come back and reinstall grub over the windows boot loader. Not a big deal but one more step.

---

### Post by cyke1 on 2010-08-19
I want to put this thread as SOLVED,  but I have few more question,  I was able to restore my system to the way it was before the problem,  but now when I put I have a 2nd drive called PQSERVICE I think this is Acers hidden partition,  is there anyway to get this back hidden and do I even need this.  Thanks again.

---

