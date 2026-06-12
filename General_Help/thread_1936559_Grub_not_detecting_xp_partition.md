---
title: "Grub not detecting xp partition"
date: 2012-03-06
forum: General Help
---

### Post by ibod on 2012-03-06
Hi 

I'm having a problem getting grub to detect my XP partition.

Original configuration:-

 Hard drive partitioned with primary partitions (Vista and Vista restore) and an extended partition for data
  did not want anything to do with Vista so 
  I Installed XP in extended partition
  Vista boot manager offered Vista or XP 
All worked for years

Decided to remove Vista and dual boot with Ubuntu 10.04 in the primary partition

Backup time 
 Backed up to usb drive using live cd and dd command 
 backed up /dev/sda5 the xp partition inside the extended partition
 backed up the hole drive /dev/sda for good measure

Install Ubuntu,
In the ubuntu install 
 removed the vista and vista restore partition to free up space
 left the extended partition with XP
 created new primary partition  as /
 created new primary partition as /home
 created new swap partition (after /home but before extended xp partition)
 installed ubuntu

Result
 Ubuntu works fine as usual
 No boot menu from grub to boot xp
 xp partition available in places menu, mounts fine

Did some searching in Google and found something that said grub can't boot 
XP in an extended partition

Back into ubuntu 
 use gparted to remove extended xp partition 
 turned swap off 
 removed swap partition
 .
 create new swap at end of drive 
 create new primary partition in the remaining space for xp 
 ( just a little larger than the old one )
 turn swap back on
 use dd to put backup (made earlier) of xp into the new primary partition

Result 
 Still no grub boot menu for XP 
 system still boots straight into ubuntu 
 xp is now no longer available in the places menu to mount

I am getting a little stuck for ideas of how to fix this 
All suggestions of how to get the XP booting as an option in grub at power on are very welcome 

Thanks Ibod

---

### Post by Bucky Ball on 2012-03-06
Open a terminal in Ubuntu and issue:

```
sudo update-grub
```

There is also a neat app called Grub Customizer. You could install that and see if Windows is there. If so, just put a tick next to it, save, restart and see what gives. 

Do you mean you are not getting a list of installed operating systems to choose from when you boot or XP is just not on the list?

---

### Post by ibod on 2012-03-06
> **Bucky Ball said:**
> Open a terminal in Ubuntu and issue:

```
sudo update-grub
```There is also a neat app called Grub Customizer. You could install that and see if Windows is there. If so, just put a tick next to it, save, restart and see what gives. 

Do you mean you are not getting a list of installed operating systems to choose from when you boot or XP is just not on the list?


Hi Thanks 

```

$ sudo update-grub
[sudo] password for  
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-39-generic
Found initrd image: /boot/initrd.img-2.6.32-39-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
done

```I would expect this to say something like 
Found windows XP image: /boot......
I guess is not going to work, but...

Ok no difference, boots straight to ubuntu  

There is no list displayed on boot, ie don't see grub at all 

Will try Grub Customizer now and report back 

Thanks Ibod

PS Does Grub Customizer work with both versions of grub 
     How do I tell which version I have 
     I think I have grub2 (ubuntu 10.04 install from live cd)

---

### Post by Bucky Ball on 2012-03-06
> **ibod said:**
> ]I would expect this to say something like 
Found windows XP image: /boot......

There is no list displayed on boot, ie don't see grub at all 

PS Does Grub Customizer work with both versions of grub 
     

1/ So would I. This obviously means grub can't locate your Win bootloader
2/ You can hold down shift (or escape depending on version) after BIOS and that should bring it up
3/ Yes, as far as I know, but if updating grub is not detecting a Win install I doubt that is going to help ...

You might also give Boot Repair a go. It's in the repos from memory or you can download and install or you can burn an ISO of it and boot from that. Totally self-contained. If there is a Windows there it should find it. Might fix things. Handy to have around anyway.

How many primary partitions do you now have on the drive, incidentally? XP is installed on a primary you say? If you open Gparted (Partition Editor) does that see the Win partition okay?

---

### Post by LostFarmer on 2012-03-06
> Vista boot manager offered Vista or XP  you must have reinstalled the Vista boot loader, when you installed XP it would have messed it up.


You have several problems.
1) your XP boot files were on your Vista partition, they are now gone.
2)formating the XP partition with linux would not write the XP volume boot code.
3)you moved XP from one drive letter (D:) to drive C: . Some times it will work and some it will not.

The first 2 are not to hard to fix, the third may require a XP primary  boot partition. 

With the first 2 problems Grub will NOT find XP.

---

### Post by Mark Phelps on 2012-03-06
From what I recall, you can't BOOT Windows from an Extended partition, it must be a Primary partition.

When you installed XP, it probably wrote the boot files to the Vista primary partition -- which is why it booted OK.

As already mentioned, you could try Boot Repair -- it may be able to repair WinXP booting.

---

### Post by LostFarmer on 2012-03-06
XP will boot from a logical volume but I would not suggest it.

With more thinking.  You have a bigger problem by using 'dd'.
The first sector of all MS partitions contains the boot code for the MS OS that formated it  (boot code may be changed when a different MS OS is installed) and a very important Bios Parameter Block (BPB).  The BPB will be different on all partitions (to be the same the partition would need to start and stop on the exact same sectors and be of the same type ie: primary/logical volume) , it further defines the partition (same as the supper block in linux).  When you used 'dd' to rewrite the partition  the BPB is now wrong.

1) The use of 'testdisk' and select options 'advanced then boot sector then rebuild' will likely correct the BPB.
the boot code still could be wrong, 'testdisk' will not correct possible problem.

OR

2) use a XP cd and make/format the partition
2b) mount the file made by 'dd'  in linux and copy the files to the XP partition.  The file made by 'dd' is basically a ISO file and can be mounted. (I have never done so)

> xp is now no longer available in the places menu to mount
 due to the BPB is wrong.

---

### Post by ibod on 2012-03-06
> **Bucky Ball said:**
> 

You might also give Boot Repair a go. It's in the repos from memory or you can download and install or you can burn an ISO of it and boot from that. Totally self-contained. If there is a Windows there it should find it. Might fix things. Handy to have around anyway.

How many primary partitions do you now have on the drive, incidentally? XP is installed on a primary you say? If you open Gparted (Partition Editor) does that see the Win partition okay?


Hi Bucky Ball 

Thanks for your help 

I am looking for boot repair to give that a go ...

you asked about partitions and gparted results 
all partitions are primary
yes gparted sees the xp fine as far as I can tell and reports used and unused sizes

From gparted 
```


Partition     File System     Mount Point   Label   Size       Used        Unused     Flags
-------------------------------------------------------------------------------------------
unallocated   unallocated                           1.00MiB
/dev/sda1     ext4            /                     19.07GiB   3.67GiB    15.40GiB
/dev/sda4     ext4            /home                 49.07GiB   1.04GiB    48.03GiB
unallocated   unallocated                           3.34MiB
/dev/sda2     ntfs                          XP      39.00GiB   20.99GiB   19.00GiB
/dev/sda3     linux-swap                            3.65GiB


```hope this table answers your question 
remember the XP was in an extended partition when I backed it up with dd, but have now restored it into a new primary

I will report back when I have found boot repair and tried that 

Hi LostFarmer 

Yes I remember having to do something to fix the boot when I installed XP as dual boot on the then Vista pc, it was a long time ago.

Your points 1 and 2  yes I see that is the case.
Point 3.  I am not sure about the drive letter moving 
when first installed and boot fixed, XP booted up as drive D  
and worked fine as far as I can remember, but again it was a long time ago




Thanks Ibod

---

### Post by oldfred on 2012-03-06
Previous posts have pointed out the issues. It may be best from Boot-Repair to post the link to a run of boot_info_script so we can see details.

You can fix everything in XP except chkdsk which probably also is required. I expect all the boot files were in the Vista partition as it had the boot flag. But you can replace them from a Windows repairCD and will have to edit boot.ini to have the correct partition. And as LostFarmer points out NTFS partitions have to have the same partition info for start & size as the partition table (fixboot & chkdsk can repair that) or testdisk can recreate it. You also need the boot flag on the NTFS partition for Windows repairs to work.

Because the partition was in a different place the backup is also not valid.
Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

or from working Ubuntu:
sudo apt-get install testdisk
sudo testdisk

Choose "proceed" on the first screen, then
"intel"
"advanced",
Select the Windows partition (although it should be selected already) and choose
"boot"
"RebuildBS"
"Write"

then press "q" a few times to quit testdisk, reboot and see whether you can boot into XP.

How to fix XP when the boot files are missing & info on windows in logical partitions-  meierfra.
[http://ubuntuforums.org/showthread.php?t=813628](http://ubuntuforums.org/showthread.php?t=813628)
missing boot files meieifra - post 10
[http://ubuntuforums.org/showthread.php?t=1241394](http://ubuntuforums.org/showthread.php?t=1241394)

---

### Post by ibod on 2012-03-06
> **oldfred said:**
> Previous posts have pointed out the issues. It may be best from Boot-Repair to post the link to a run of boot_info_script so we can see details.

You can fix everything in XP except chkdsk which probably also is required. I expect all the boot files were in the Vista partition as it had the boot flag. But you can replace them from a Windows repairCD and will have to edit boot.ini to have the correct partition. And as LostFarmer points out NTFS partitions have to have the same partition info for start & size as the partition table (fixboot & chkdsk can repair that) or testdisk can recreate it. You also need the boot flag on the NTFS partition for Windows repairs to work.

Because the partition was in a different place the backup is also not valid.
Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

or from working Ubuntu:
sudo apt-get install testdisk
sudo testdisk

Choose "proceed" on the first screen, then
"intel"
"advanced",
Select the Windows partition (although it should be selected already) and choose
"boot"
"RebuildBS"
"Write"

then press "q" a few times to quit testdisk, reboot and see whether you can boot into XP.

How to fix XP when the boot files are missing & info on windows in logical partitions-  meierfra.
[http://ubuntuforums.org/showthread.php?t=813628](http://ubuntuforums.org/showthread.php?t=813628)
missing boot files meieifra - post 10
[http://ubuntuforums.org/showthread.php?t=1241394](http://ubuntuforums.org/showthread.php?t=1241394)



Hi 

One point, I would consider my self as quite new at this level and am not totally clear on all the information.

First I have run testdisk to try to fix the partition data for the dd'ed xp in it's new primary partition

I was hoping this would make the xp partition available to mount in places, as it was before I deleted the extended partition and dd'ed xp back into a primary partition, but its still not there.

Then I ran the Boot-Repair and rebooted. Grub menu appeared automatically but still no XP entry. 
Booted ubuntu and looked in places still no XP

Boot info script   @  [http://paste.ubuntu.com/871815](http://paste.ubuntu.com/871815)

Not sure if I was supposed to boot a windows repair console and run chkdsk at this point or get the boot from grub and xp visible in places first, so I will hold off on that until you have looked at the boot info script

Thanks for all your help

Ibod

---

### Post by oldfred on 2012-03-06
You need to move boot flag to NTFS partition for any Windows tools to see the partition. Windows only boots, repairs or installs to the active partition which is the boot flag in MBR partitioning. Use gparted, Disk Utility or command line (Linux or in Windows commands active partition) to move boot flag.

Script shows no XP boot files. They were in the Vista partition you deleted as Windows literally moves boot files to the active partition on 2nd installs.

WinXP - you need these three files in XP to boot.
/boot.ini /ntldr /NTDETECT.COM

Also boot.ini has to have info in it to the correct drive & partition. You can edit from Linux but have to be careful to save with Windows line endings. Or you can run the full set of XP repairs.

If editing windows files like boot.ini
(Use nano instead of gedit, it's better for dos-style linebreaks)
Linux, of course, uses only LF as newline and DOS is expecting CR/LF so text files look wrong in DOS.
New versions of gedit have an combo box under save as to cchoose windows format.

How to edit the Boot.ini file in Windows XP
[http://support.microsoft.com/kb/289022/](http://support.microsoft.com/kb/289022/)

XP repair floppy disk if you have one:
[http://support.microsoft.com/kb/310994](http://support.microsoft.com/kb/310994)
XP CD fixboot 
[http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html](http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html)
Description of the Windows XP Recovery Console for advanced users list of commands
[http://support.microsoft.com/kb/314058/](http://support.microsoft.com/kb/314058/)

You almost for sure also need to run chkdsk.

---

### Post by ibod on 2012-03-07
> **oldfred said:**
> You need to move boot flag to NTFS partition for any Windows tools to see the partition. Windows only boots, repairs or installs to the active partition which is the boot flag in MBR partitioning. Use gparted, Disk Utility or command line (Linux or in Windows commands active partition) to move boot flag.

Script shows no XP boot files. They were in the Vista partition you deleted as Windows literally moves boot files to the active partition on 2nd installs.

WinXP - you need these three files in XP to boot.
/boot.ini /ntldr /NTDETECT.COM

Also boot.ini has to have info in it to the correct drive & partition. You can edit from Linux but have to be careful to save with Windows line endings. Or you can run the full set of XP repairs.

If editing windows files like boot.ini
(Use nano instead of gedit, it's better for dos-style linebreaks)
Linux, of course, uses only LF as newline and DOS is expecting CR/LF so text files look wrong in DOS.
New versions of gedit have an combo box under save as to cchoose windows format.

How to edit the Boot.ini file in Windows XP
[http://support.microsoft.com/kb/289022/](http://support.microsoft.com/kb/289022/)

XP repair floppy disk if you have one:
[http://support.microsoft.com/kb/310994](http://support.microsoft.com/kb/310994)
XP CD fixboot 
[http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html](http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html)
Description of the Windows XP Recovery Console for advanced users list of commands
[http://support.microsoft.com/kb/314058/](http://support.microsoft.com/kb/314058/)

You almost for sure also need to run chkdsk.


Hi oldfred

Am trying to follow your last post, had a go at the above but there must be something I am not understanding here.

Have set the boot flag to the NTFS partition and run the windows recovery console 

as your XP CD fixboot link. with pc booted in windows recovery console:-

I was not to sure about the optional device in step 4 so just did "fixmbr"
then step 5  "fixboot D:" as the XP was installed on D: this did not recognise D: so I tryed "fixboot C:" which seemed to work. But I with hindsight I think this was not correct 

PC then wouldn't boot at all, error NTLDR missing, I fixed that with boot-repair by reinstalling grub2. with the live cd.  Ubuntu now boots ok

Now gparted can't see the data in the xp partition, so I think I  have broken something else. 
Screen shot of the current gparted state here  **[http://tinyurl.com/76sypgv](http://tinyurl.com/76sypgv) **and the original state is image 2 

current boot-repair output here [http://paste.ubuntu.com/873360](http://paste.ubuntu.com/873360)

Just a reminder note that I have two backups made before I started, as in post 1.

I don't wont to go back to these, as I would prefer to stick with it and learn something, rather than chicken out just because it's not easy.

Thanks Ibod

---

### Post by oldfred on 2012-03-07
You still are missing the three boot files:

WinXP - you need these three files in XP to boot.
/boot.ini /ntldr /NTDETECT.COM

Windows repair should add them, but you may need to run BOOTCFG  /rebuild to reset boot.ini or manually edit boot.ini.

windows needs three things. NTFS primary partition with boot flag. Partition PBR partition boot sector set as valid NTFS partition and the boot files. This assumes the rest of the install is still there.

meierfra. - How to fix XP when the boot files are missing + download
[http://ubuntuforums.org/showthread.php?t=813628](http://ubuntuforums.org/showthread.php?t=813628)
missing boot files meieifra - post 10
[http://ubuntuforums.org/showthread.php?t=1241394](http://ubuntuforums.org/showthread.php?t=1241394)

---

### Post by ibod on 2012-03-10
> **oldfred said:**
> You still are missing the three boot files:

WinXP - you need these three files in XP to boot.
/boot.ini /ntldr /NTDETECT.COM

Windows repair should add them, but you may need to run BOOTCFG  /rebuild to reset boot.ini or manually edit boot.ini.

windows needs three things. NTFS primary partition with boot flag. Partition PBR partition boot sector set as valid NTFS partition and the boot files. This assumes the rest of the install is still there.

meierfra. - How to fix XP when the boot files are missing + download
[http://ubuntuforums.org/showthread.php?t=813628](http://ubuntuforums.org/showthread.php?t=813628)
missing boot files meieifra - post 10
[http://ubuntuforums.org/showthread.php?t=1241394](http://ubuntuforums.org/showthread.php?t=1241394)

Hi oldfred

I have got the three files in place, (downloaded from the link in your above post)
edited boot.ini to point at partition(2) (/dev/sda2 the XP partition) done in nano
updated grub that can now see XP.
did a chkdsk from Windows recovery console, (found several errors all fixed) 
fixed the BPB with testdisk
and booted 

XP is now in the grub menu and 'sort of bootable'.
1st  boot just went straight back to grub
2nd  boot went to the windows "We apologize for the inconvenience, but  Windows did not start successfully. A recent hardware or software change  might have caused this." screen 
Offering Safe mode, Safe mode with  networking, Safe mode with Command prompt, Last known good configuration  and Start Windows Normally. 
All of these options loop back to grub

Is it possible that there is something incorrect in one of the 3 boot files ?

Does the fact that the xp was originally installed after Vista and therefore installed as D: make any difference to what we have done ?

Are there any other files or logs that would help

[http://paste.ubuntu.com/877622/](http://paste.ubuntu.com/877622/)      
for latest boot-repair log encase it sheds any light


Thanks Ibod

---

### Post by oldfred on 2012-03-10
You have to run chkdsk until there are no errors.

Script is showing a Vista/7 type boot sector. I know I compared my XP PBR before and after running chkdsk from a Windows 7 repairCD and it converted my PBR to Windows 7. As I remember it still booted but I converted it back to XP. One of the main differences was it called out bootmgr to boot not ntldr. But structure is also somewhat different.

Either fixBoot from the XP CD or from a Windows 7 repairCD.

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
Use bootsect.exe to repair XP & older or Vista/7 bootsectors - Use diskpart, then list volumes to see which drive to use 
bootsect.exe /nt52 c:  *compatible* with operating systems older (XP) than Windows Vista.
bootsect.exe /nt60 c:  *compatible* with Windows Vista, Windows Server 2008 or later

---

### Post by ibod on 2012-03-11
> **oldfred said:**
> You have to run chkdsk until there are no errors.

Script is showing a Vista/7 type boot sector. I know I compared my XP PBR before and after running chkdsk from a Windows 7 repairCD and it converted my PBR to Windows 7. As I remember it still booted but I converted it back to XP. One of the main differences was it called out bootmgr to boot not ntldr. But structure is also somewhat different.

Either fixBoot from the XP CD or from a Windows 7 repairCD.

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
Use bootsect.exe to repair XP & older or Vista/7 bootsectors - Use diskpart, then list volumes to see which drive to use 
bootsect.exe /nt52 c:  *compatible* with operating systems older (XP) than Windows Vista.
bootsect.exe /nt60 c:  *compatible* with Windows Vista, Windows Server 2008 or later


Hi oldfred 

Yes I run the chkdsk twice, first time "found one of more errors" second time no errors found.

The Windows Vista/7 boot could have came from the original Vista that was on the pc at purchase. I installed XP in the existing second extended/logical partition because Vista was not wanted. Had to use some boot manager tool to make it boot as the XP install after Vista of cause stopped it from booting. (that was years ago)

Then at last I decided to lose the Vista for good and dual boot with Ubuntu (the subject of this thread)

Did dd backup of the XP in its logical partition, and dd backup of the whole drive for good measure.

Saw some threads that said XP could not be booted in a extended partition when googling because i was having boot problems

so removed the extended partition and and created a primary in gparted and dd'ed xp back 

I would have thought that this would have removed the Vista boot, especially having installed ubuntu in the original Vista partition 

I used an original Windows XP home edition CD to do the repair console work. 
I was originally using an SP2 CD but mislaid this and subsequently used a SP1 CD.
I believe these are identical with regard to the operations we are doing ?
I did use boot-repair in post 6 that may be where the Vista boot came from 

I will fixboot from recovery console and report back 

Thanks for all your help

---

### Post by oldfred on 2012-03-11
Either fixBoot from Windows or even testdisk can rebuild a PBR. Windows has to have a valid NTFS signature and part of that is the partition start & size. If you dd'd it from somewhere else the start and maybe size would be wrong and need repair of the PBR.

---

### Post by ibod on 2012-03-11
> **oldfred said:**
> Either fixBoot from Windows or even testdisk can rebuild a PBR. Windows has to have a valid NTFS signature and part of that is the partition start & size. If you dd'd it from somewhere else the start and maybe size would be wrong and need repair of the PBR.

I used testdisk to fix the PBR so that should be ok will look for a log for that 

When running fixboot in windows recovery console fixboot asks :-

"The target partition is C:. Are you sure you want to write a new boot sector to the partition c: ?"

I am not sure about this because :-

When I installed XP originally (years ago) it has always been D: because the pre existing Vista was C: 

Do I say "Yes"  to this prompt or is there a switch for the fixboot to make it see D:  ?

---

### Post by oldfred on 2012-03-11
The first or only install of Windows is c:. So unless you still have another install I would think you need to write it to c:.

You may have to update boot.ini with bootcfg as it may still refer to the old partition.

FIXMBR  C:  #do not run if you still want grub in the MBR
FIXBOOT  C:
BOOTCFG  /rebuild  # rebuilds boot.ini
chkdsk c: /r

A discussion about the Bootcfg command and its uses fix boot.ini
[http://support.microsoft.com/kb/291980](http://support.microsoft.com/kb/291980)
[http://pcsupport.about.com/od/fixtheproblem/ht/repairbootini.htm](http://pcsupport.about.com/od/fixtheproblem/ht/repairbootini.htm)

---

### Post by ibod on 2012-03-11
> **oldfred said:**
> The first or only install of Windows is c:. So unless you still have another install I would think you need to write it to c:.

You may have to update boot.ini with bootcfg as it may still refer to the old partition.

FIXMBR  C:  #do not run if you still want grub in the MBR
FIXBOOT  C:
BOOTCFG  /rebuild  # rebuilds boot.ini
chkdsk c: /r

A discussion about the Bootcfg command and its uses fix boot.ini
[http://support.microsoft.com/kb/291980](http://support.microsoft.com/kb/291980)
[http://pcsupport.about.com/od/fixtheproblem/ht/repairbootini.htm](http://pcsupport.about.com/od/fixtheproblem/ht/repairbootini.htm)


Hi oldfred

```

fixboot C: 

The file system on the startup partition is unknown. 
Fixboot is attempting to detect the file system type. 
The boot sector is corrupt.
Fixboot is checking the file system type...
The partition is using the NTFS file system.
Fixboot is writing a new boot sector
The new boot sector was successfully written. 

```looks like that worked 

```

bootcfg /rebuild

Scanning all disks for windows installations.
Please wait, since this may take a while...
ERROR: Failed to successfully scan disks for windows instillations
This error may be caused by a corrupt file system, which would prevent bootcfg from successfully scanning. 
Use chkdsk to detect any disk errors.
NOTE: This operation must complete successfully in order for the /add or /rebuild commands to be utilised.

```But this one did not work 

Run chkdsk c: /r
which found one or more errors 
run chkdsk c: /r  again 
found no errors but did jump backwards in % done while running 
run chkdsk c: /r 3rd time, no errors reported again but still jumped back as before 

re-run  bootcfg /rebuild

which reported the same error as before (see above)

exited recovery console 


and re started back into the recovery console but this time the entry into the console was not the same 

this time the recovery console listed the windows installation and asked which one I wanted to log into  and asked for the admin password 
this is the first time this has happened 
I know it is normal and have been wondering why the step was missing 

does any of this shed any light on what is wrong.

Ibod

---

### Post by oldfred on 2012-03-11
You may be able to manually edit boot.ini?

If you edit from Linux:
If editing windows files like boot.ini
(Use nano instead of gedit, it's better for dos-style linebreaks)
Linux, of course, uses only LF as newline and DOS is expecting CR/LF so text files look wrong in DOS.
New versions of gedit have an combo box under save as to cchoose windows format.

How to edit the Boot.ini file in Windows XP
[http://support.microsoft.com/kb/289022/](http://support.microsoft.com/kb/289022/)

The partition number has to match your partition that Windows is installed in.

---

### Post by ibod on 2012-03-12
> **oldfred said:**
> You may be able to manually edit boot.ini?

If you edit from Linux:
If editing windows files like boot.ini
(Use nano instead of gedit, it's better for dos-style linebreaks)
Linux, of course, uses only LF as newline and DOS is expecting CR/LF so text files look wrong in DOS.
New versions of gedit have an combo box under save as to cchoose windows format.

How to edit the Boot.ini file in Windows XP
[http://support.microsoft.com/kb/289022/](http://support.microsoft.com/kb/289022/)

The partition number has to match your partition that Windows is installed in.

Hi oldfred 

Looks like I am getting very close to solving this now 
but Windows clings on to not quite starting

I can now get to a screen that looks like the XP logon screen with the dark blue bar at the top and bottom, and the light blue middle section. 
With "Windows XP" text and the windows flag symbol above the text.
But the "Turn off computer", & "After you log on, you can..." missing from the bottom bar, and the "To  begin, clickyour user name" and all logon icons are missing from the screen. 


If I press ALT+TAB to see what is behind this screen, there is a logon to windows screen with two text entry boxes. (This is not the same as the old style NT logon screen) 

When I let go of the ALT key this screen drops back behind again so there is no way to enter a user name and password 

Anyone seen this behaviour before, have been googling without much success, accept that something may have disabled the user account from loging on in some way.

ctrl + alt+ del log on screen also does not work

Ibod

---

### Post by oldfred on 2012-03-12
It may be some mismatch of a file somewhere. Not sure how to check for that type of issue.

---

### Post by ibod on 2012-03-12
> **oldfred said:**
> It may be some mismatch of a file somewhere. Not sure how to check for that type of issue.


Hi oldfred 


Many thanks for your help for getting me this far and thanks to all that have contributed to this thread. I will continue to work on this for a while, as it still looks like it might work out ok in the end. 

I will update this thread if I find the solution

I have learned quite a lot in the last few days so many thanks to all for that as well

---

