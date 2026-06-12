---
title: "Need some MAJOR hard drive help."
date: 2012-07-18
forum: General Help
---

### Post by abkarch on 2012-07-18
OK here I go. 
I have this ubuntu live CD im typing from for circumstances like this.
For some reason, acer created my PCs (its a laptop) hard drive as an MBR drive on a UEFI bios (i think its uefi 1.0, not 2.0, although i hardly know the difference). Meaning i could not dual boot windows 8 alongside windows 7, because win8 can only use a GPT drive on a uefi bios. 

So i thought i would go about a way looking to change the drive to GPT from MBR. I had thought about in the past, but i didnt do it and i didnt remember why i previously changed my mind until I made this mistake.

I used gdisk from windows in an attempt to convert from MBR to GPT. I got to the point where it said confirm operation, and then told myself i didnt really know what i was doing (i had completely at the time forgotten this was my BOOT drive, the OS i was currently using). So at the Y/N screen i typed exit (had no idea what to type) then it Said just Y/N by itself, so i assumed it read the exit command and typed Y. it then proceeded to continue with the GPT conversion operation. my computer bluescreened almost instantly and i restarted, only to be greeted with "No operating system found." 

oh and these are the instructions that i used (obviously didnt notice it was not a boot drive) [http://www.sevenforums.com/general-discussion/222853-convert-drive-gpt-guild-without-losing-data.html#post1868308](http://www.sevenforums.com/general-discussion/222853-convert-drive-gpt-guild-without-losing-data.html#post1868308)

So ive learned my lesson and am obviously done messing with HDDs partition tables (I think thats what they are called) for a long while. So the deal is, all of my files are still in the drive and are located and read by Ubuntu, including the windows files. Also, ubuntu reads the drive as a GPT drive. I opened Gdisk again from the live CD (because i figured since i was not doing it from the drive anymore, i COULD complete the operation this time. It gives several problems and warnings and then aborts the operation. 

```
Problem: partitions 2 and 1 overlap:
  Partition 2: 1917848077 to 2462285169
  Partition 1: 1936269394 to 3772285809

Problem: partitions 3 and 1 overlap:
  Partition 3: 1818575915 to 2362751050
  Partition 1: 1936269394 to 3772285809

Problem: partitions 3 and 2 overlap:
  Partition 3: 1818575915 to 2362751050
  Partition 2: 1917848077 to 2462285169

Problem: partitions 4 and 1 overlap:
  Partition 4: 2844524554 to 2844579527
  Partition 1: 1936269394 to 3772285809

Problem: partition 1 is too big for the disk.

Problem: partition 2 is too big for the disk.

Problem: partition 3 is too big for the disk.

Problem: partition 4 is too big for the disk.

Warning! Secondary partition table overlaps the last partition by
2827463571 blocks!
You will need to delete this partition or resize it in another utility.

Caution: Partition 1 doesn't begin on a 8-sector boundary. This may
result in degraded performance on some modern (2009 and later) hard disks.

Caution: Partition 2 doesn't begin on a 8-sector boundary. This may
result in degraded performance on some modern (2009 and later) hard disks.

Caution: Partition 3 doesn't begin on a 8-sector boundary. This may
result in degraded performance on some modern (2009 and later) hard disks.

Caution: Partition 4 doesn't begin on a 8-sector boundary. This may
result in degraded performance on some modern (2009 and later) hard disks.

Consult http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/
for information on disk alignment.

Identified 9 problems!

```So yea, thats it. My main goal is to get my installation back without losing data. And i feel if I could fix the problems that gdisk mentions without deleting the data, then I could actually finish the GPT conversion From the disk, or convert it back to MBR, i dont care, i just want my working PC back. And i dont really care for windows 8 anymore either, i was simply curious and very bored at the time. 

And I would appreciate a more specific answer then "you're screwed."

I dont think i left anything out. Please let me know if any other info is needed. Thanks for any help! Im hardly a linux user so holding my hand is appreciated :D

---

### Post by mwl128340 on 2012-07-18
not sure if i can help you but your gunna have to give more info than that. running fdisk and bootinfoscript could give more info on what is happening.
```
sudo fdisk -l
```

[http://sourceforge.net/projects/bootinfoscript/]("http://sourceforge.net/projects/bootinfoscript/")

---

### Post by abkarch on 2012-07-18
fdisk says

```
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x30be30bd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   976773167   488386583+  ee  GPT

```will post with bootinfoscript in a minute..if someone can tell me how to use it after its extracted.

wierd thing is SDA3 is my actual windows partition, I dont know if thats relevant.

---

### Post by westie457 on 2012-07-18
Take a look at testdisk to revover your old partition table. Full instructions are here. [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by abkarch on 2012-07-18
that looks promising. How do i use the tar.gz archive with terminal? do I need to extract it somewhere?

---

### Post by westie457 on 2012-07-18
testdisk is available from the repositories and works from a LiveCD Desktop. No need to use a tar.gz file. It will only write changes when you tell it to.

---

### Post by abkarch on 2012-07-18
it says unable to locate package testdisk. do i need to add a repo or something?

---

### Post by oldfred on 2012-07-18
Testdisk is in this:
enable the "universe" repository to download testdisk
System>Administration>Software Sources>Ubuntu Software.

Windows often does not delete backup gpt table. One of the advantages of gpt is that it has a backup at the end of the drive. Windows in converting from gpt to MBR only deletes the primary and ignores the backup. But Linux tools see the backup and get confused.

You should only attempt the conversion from MBR to gpt with a Linux liveCD. But Windows will only boot from gpt with UEFI and it has to be version 2 or better.
Also post this:
sudo gdisk -l /dev/sda

GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)
repair gpt:
[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html)

---

### Post by abkarch on 2012-07-18
im confused as how to access system>administration>Software sources. Is that in a toolbar somewhere or something? O.o

ah never mind i figured out how to enable through software center i think.

---

### Post by abkarch on 2012-07-18
testdisk did nothing. i said write partition table and it said i most reboot to fix changes, no fix.

Oh, and i did forget to say that i would use the windows 7 recovery disc for the bootrec commands. but it says i must use a compatible version of windows.
is there anything i can do with gdisk? i looked around and it appears there are a few options for fixing but i dont know if it will delete the data or not. this is what the command said:
```
Caution: invalid backup GPT header, but valid main header; regenerating
backup header from main header.

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: damaged

****************************************************************************
Caution: Found protective or hybrid MBR and corrupt GPT. Using GPT, but disk
verification and recovery are STRONGLY recommended.
****************************************************************************
Disk /dev/sda: 976773168 sectors, 465.8 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 6B925656-6E75-E949-A893-366EE448BCF5
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 976773134
Partitions will be aligned on 2048-sector boundaries
Total free space is 2036 sectors (1018.0 KiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048        31746047   15.1 GiB    0700  
   2        31746048        31950847   100.0 MiB   0700  
   3        31950848       976773112   450.5 GiB   0700  
```

---

### Post by oldfred on 2012-07-18
To get a better picture of where everything is at, post link that BootInfo creates. This is not to repair boot, but it also creates a nice report of how system is partitioned an what errors may be found.

Boot Repair -Also handles LVM, GPT and separate /boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration.

---

### Post by abkarch on 2012-07-18
[http://paste.ubuntu.com/1099295/](http://paste.ubuntu.com/1099295/)
it mentioned repairing MBR in the repair process, so do you guys think i should reboot and see what happens? (I would rather not unless you believe the problem is solved, ive got alot of things to do every time i reboot live CD). just wanting an OK if i should.

after i repaired though, ran summary again and it said same thing...so im guessing problem isnt solved, unless i MUST reboot.

---

### Post by abkarch on 2012-07-18
just rebooted, no change, windows repair disk still says i must use compatible version of windows, no operating system found, gparted says GPT disk.

---

### Post by oldfred on 2012-07-18
Windows only boots from gpt partitioned drives with UEFI or very new system. If you have BIOS you have to have MBR partitioning.

So you need to convert back to MBR partitions.

Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)
You then need to use gdisk to convert from gpt to MBR
[http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr](http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr)

Then your Windows repairs may work. With MBR the boot flag indicates to the Windows boot loader which partition to boot. So you will need the boot flag on sda2 or sda3. In Windows repairs it is make active or some such command. Normally Windows 7 has a 100MB boot partition, your sda2 with 2 of the 3 required boot files. But your sda3 also has those boot files and may also be directly bootable (if so the sda2 then is obsolete).

Vista/7 (with 7 the first two files are usually in a separate 100MB boot partition)
/bootmgr /Boot/BCD /Windows/System32/winload.exe

---

### Post by abkarch on 2012-07-19
Thanks, i had no idea that a uefi version 2 or higher was required. anyway, i just want to make sure that the GPT to MBR operation is completeable without deleting all my data?

---

### Post by YannBuntu on 2012-07-19
Hello
That is not a "zero-risk" operation. You should backup your documents first.

---

### Post by oldfred on 2012-07-19
Because gdisk said this, the risk is even higher, so backup is more important. I would try to remove hybrid MBR which has many issues and fix errors before attempting to convert. Converison may only work at all with all errors resolved.

> Caution: Found protective or hybrid MBR and corrupt GPT. Using GPT, but disk
verification and recovery are STRONGLY recommended.

---

### Post by abkarch on 2012-07-19
i believe from other tasks i did using things like testdisk/gdisk that it is a protective MBR, either way, i guess i was just trying to figure out how to solve the errors.

---

### Post by abkarch on 2012-07-19
OK i did the procedure and my PQSERVICE and SYSTEM RESERVED partitions are both happy and healthily read as NTFS and the drive is now read as a MBR. making progress. I told Disk utility to change the filesystem  from EFI to NTFS because im having some problems reading the primary windows/data partition, it was reading as a EFI in disk utility...any ideas? its still trying to change the filesystem...how long should this take?
EDIT: after typing this post, i got a timeout error from Disk utility, but its still going...whats that mean?

---

### Post by oldfred on 2012-07-19
EFI in gparted is just seen as a boot flag, really a gpt code of ef00. But a boot flag in MBR is not the same as a 'boot flag' in gpt for efi boot. If that makes sense.

The boot flags do not have anything to do with formating. The efi partition is normally FAT32. Windows boot partitions all now all NTFS.

I use Disk Utility only occasionally  to change flags or add labels. Some have had issues so for anything else I use gparted.

---

### Post by abkarch on 2012-07-19
Ok so the current deal is that ubuntu reads all partitions except "Unknown" (my windows/data partition). I gave it a boot label in Gparted which is why the boot thing sort of works now.... On boot up i get a black screen with a flickering line on the top left. The windows recovery disk now enables me to get to a command prompt HOWEVER it does not detect windows installations when i try to scan for OS or rebuild the BCD. What should i do?

---

### Post by abkarch on 2012-07-19
Holy crap, I fixed it. typing from my windows 7 installation, with every single one of my 350k+ files intact. 

Not really sure what happened, but ill leave this here....i used gdisk from the ubuntu live CD to change back to an MBR, which you can find help with in one of the above links. Anyway, after that i gave my C:\ its bootable tag back in Gparted, then i used the windows 7 recovery CD to run the following command from a command prompt. "chkdsk C: /f" without quotes. Anyway after that finished it found my windows installation and i used these commands:
bootrec /fixmbr
bootrec /rebuildbcd
bootrec /fixboot

And i shut down and removed the disk, and windows 7 booted right up. I doubt this will be helpful to anyone, but ill leave it here just in case.

---

