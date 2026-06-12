---
title: "Gparted unrecognized disk label error"
date: 2012-02-08
forum: General Help
---

### Post by djpemberton on 2012-02-08
I had gotten a new laptop. I removed the hard drive and replaced it with a solid state. I put the extra hard drive in an enclosure and "erased" everything with Gparted. I then had Gparted make a new partition table (MSDOS). Then, I tried to create a FAT32 partition so that I can use it as data storage for any of my computers. Gparted could not complete that last operation. It gave this error: "unrecognized disk label". 

What can I do to fix this? The hard drive is practically brand new, as I only booted from it once before removing it from the new laptop.

---

### Post by oldfred on 2012-02-08
I would use NTFS unless you are also sharing with a Mac or xBox. FAT32 cannot store a file over 4GB and does not have a journal so repairs are more difficult.

I think FAT has more limits on characters and they all have to be caps. What label were you assigning?

I still have one old FAT partition (all data is actually now in NTFS. It is labeled as SHARE.

```
Device           UUID                                   TYPE       LABEL
/dev/sda4        46CD-C9B2                              vfat       SHARE
```

---

### Post by djpemberton on 2012-02-09
OK, I tried to format it to ntfs with Gparted simply by right clicking and selecting "Format To" and ntfs. It says (as it did previously) that everything was completed successfully. However, when Gparted scans everything again (as it always does when completed) there is a warning label. Here is the warning:

"Unable to detect file system! Possible reasons are:
-The file system is damaged
-The file system is unknown to Gparted
-There is no file system available (unformatted)
-The device entry /dev/sdb1 is missing"

I don't get it?

---

### Post by oldfred on 2012-02-09
What SSD is it. 

There are a few SSDs with build in RAID that do not work well with anything other than the default build in RAID.

Post this:
sudo parted /dev/sdb unit s print

---

### Post by djpemberton on 2012-02-09
It isn't my solid state drive. That one was placed in my laptop. This is a Seagate Momentus 750GB SATA that came out of my Asus U46E.

Here is what you asked for. Thanks in advance.

---------
Model:  Mass Storage Device (scsi)
Disk /dev/sdb: 1465149166s
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start  End          Size         Type     File system  Flags
 1      2048s  1465147391s  1465145344s  primary
-------------

---

### Post by oldfred on 2012-02-09
Did you post the full output from parted? It does not show several things.

Mine:

```
fred@fred-LT-A105:~$ sudo parted /dev/sda unit s print
Model: ATA FUJITSU MHV2160B (scsi)
Disk /dev/sda: 312581808s
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start       End         Size        Type      File system     Flags
 1      63s         113595614s  113595552s  primary   ntfs            boot
 2      113595615s  175028174s  61432560s   primary   ntfs
 3      175028236s  312062624s  137034389s  extended
 5      175028238s  205744454s  30716217s   logical   ext4
 6      205744518s  211881284s  6136767s    logical   linux-swap(v1)
 7      211881348s  312062624s  100181277s  logical   ext3

```

I have had drives that were once in RAID not work because of metadata on drive and had Windows drives not work because they needed chkdsk from Windows. Ubuntu/gparted will not mount a Windows drive if it needs chkdsk so you do not cause issues that chkdsk may not be able to fix.

---

### Post by djpemberton on 2012-02-09
Yes, that was the full output. If the problem is with it being a Windows drive, how do I fix it so that I can mount it on Ubuntu. Do I need to use programs from a Windows box?

Thanks.

---

### Post by oklokl on 2012-02-09
mkfs.vfat /dev/sdaX
gparted bug..

dd if=/dev/zero of=/dev/sdb bs=446 count=1234
and rebooting



Low-level format

dd if=/dev/zero of=/dev/sdb bs=1M
Precautions
not stop the..

or 
test..

umount -i /dev/sdb
badblocks -vw /dev/sdb

---

### Post by djpemberton on 2012-02-09
Come again?

---

### Post by oldfred on 2012-02-10
oklokl is a little to concise in his posts. oklokl please add some explanation so new users understand what you are suggesting.

He is using command line to format, using dd (which I find powerful but dangerous) to erase drive. If you put in the wrong drive, it will erase the wrong drive so typos can be dangerous with dd.

Did you create a partition or two before you tried formating? It seemed like the error message was that you were formating drive not partiton?

---

### Post by djpemberton on 2012-02-10
OK, I had used Windows 7 to format the disk to ntfs. When I plugged it back in to my Ubuntu box, nothing happened. Gparted didn't see it. Nothing. However, today I plugged it back in to try some of the commands and, after a little time, Ubuntu auto mounted it and I was able to copy some test files to it.

Then, I "safely removed" it. I tried plugging in back in and Ubuntu gave me this error: 

"Error mounting: mount exited with exit code 13: ntfs_mst_post_read_fixup: magic: 0x00000090  size: 1024  usa_ofs: 88  usa_count: 65535: Invalid argument
Record 6 has no FILE magic (0x90)
Failed to open inode FILE_Bitmap: Input/output error
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows then reboot into Windows twice. The usage of the /f parameter is very important! If the device is a SoftRAID/FakeRAID then first activate it and mount a different device under the /dev/mapper/ directory, (e.g. /dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation for more details."

I'm not totally sure what all this means and what exactly to do, especially if the second is the problem.

---

### Post by oklokl on 2012-02-10
> **oldfred said:**
> oklokl is a little to concise in his posts. oklokl please add some explanation so new users understand what you are suggesting.

He is using command line to format, using dd (which I find powerful but dangerous) to erase drive. If you put in the wrong drive, it will erase the wrong drive so typos can be dangerous with dd.

Did you create a partition or two before you tried formating? It seemed like the error message was that you were formating drive not partiton?

Answer
 A good point.

but..

Partition Error ..and bad Sector
 Solution

gparted error..

Low-level format
 There is no solution

Not recommended
dd if..

---

### Post by djpemberton on 2012-02-10
OK, so I ran chkdsk /f on the drive and restarted twice from a Windows 7 computer. It seemed like this may have worked, but Windows will not allow me to access the drive. "D:\ is not accessible. Access is denied."

---

### Post by djpemberton on 2012-02-10
I don't understand anything that oklokl writes!

---

### Post by oklokl on 2012-02-10
> **djpemberton said:**
> I don't understand anything that oklokl writes!

sorry..

Answer
 Partition
 error .. or .. sector mbr error

Hardware error code
HDD BIOS memory buffer or Pc memory buffer -> error bug regeneration
bad sector

Recovery is difficult.
get tangled error..

Cleanly
If you do not clear
The error is repeated
There is a possibility

---

### Post by oldfred on 2012-02-10
Did you also run chkdsk on the d: partition. It normally defaults to c: unless you specify otherwise. Also if any errors you have to rerun it until you get no errors as it cannot fix everything on one pass.

The errors posted at the beginning were possibilities not all the errors. So first chkdsk, then see if drive is showing issues with Smart Status and hard ware faults and possibly others. If all that fails then scrubbing drive and trying again may be the only choice.

---

### Post by djpemberton on 2012-02-10
Yes, I made sure I was using the right drive letter each time. I have done it 3 times, but Windows still wouldn't allow me to access the drive.

I plugged it into my Ubuntu box and it opened fine again. I safely ejected it and inserted it again. It worked fine the second time. Just for safe measure, I did it a third time and it reported the same long error it had before.

Does that tell you anything useful?

---

### Post by oldfred on 2012-02-10
Beyond chkdsk I am out of ideas.

What does Smart Status show in Disk Utility?

---

### Post by djpemberton on 2012-02-10
Because I cannot mount it currently, I cannot do the Smart Scan. I really wish there was something that could be done!

---

### Post by djpemberton on 2012-02-10
Is there a better way for me to format and partition it? In the disk utility it gives me the option to Format the drive according to several schemes (MBR, GUID, Apple, or don't partition). I just need to use it for data storage.

---

### Post by oldfred on 2012-02-10
MBR has been the standard since hard drives on PCs in the '80s. gpt or GUID is the newer system. Ubuntu will boot from gpt in BIOS or UEFI mode, but Windows 64 bit requires UEFI. If just data either Ubuntu or Windows should read it ok. XP does not know about gpt and does not work with it. But either should not make a difference.

You should be able to see drive in Disk Utility?

---

### Post by xyzzyman on 2012-02-10
I wonder if the external adapter is what's causing the issue? I've had some off brand ones that were extremely finicky. 

You could also try putting the HDD back in, and using a livecd to repartition and set it up.

There have been a few times I had to do a DBAN (Duke Boot & Nuke) on a drive before I could get Windows or Ubuntu to be able to repartition it. Only let it run for a minute to wipe out anything at the beginning of the drive. WD's boot disc also has a function that only works on WD drives that does a similar.

---

### Post by oklokl on 2012-02-11
gparted The default
mbr..

usb Stick
default
mbr and.. fat32..

The default value
When you escape.

eror code.. 

I do not know the cause

Errors that occurred
 gpt and mbr and will occur regardless of

---

### Post by djpemberton on 2012-03-20
OK, I've been away for a bit. I tried putting the HD back into my laptop. I formatted it to ntfs with a live cd. After putting the other HD back into the laptop and putting this one back into the external enclosure, I plugged it in. Ubuntu automatically mounted it. I was able to copy files to it without issues. I then selected to safely remove the drive in Ubuntu. Once that was apparently finished, I waited a bit and tried to plug it back in. It wasn't auto mounted so I tried to manually mount it. Then, I got the exact same error as before. 

Are we out of ideas?

---

### Post by Bobhuber on 2012-03-20
> **djpemberton said:**
> OK, I've been away for a bit. I tried putting the HD back into my laptop. I formatted it to ntfs with a live cd. After putting the other HD back into the laptop and putting this one back into the external enclosure, I plugged it in. Ubuntu automatically mounted it. I was able to copy files to it without issues. I then selected to safely remove the drive in Ubuntu. Once that was apparently finished, I waited a bit and tried to plug it back in. It wasn't auto mounted so I tried to manually mount it. Then, I got the exact same error as before. 

Are we out of ideas?
It looks like you have almost answered your own question. After reading all the posts the only common denominator is the external enclosure.

---

### Post by oldfred on 2012-03-21
When you unmount a drive and then plug it back in it does not auto mount it again, so that is normal.

What error are you getting. The disk label error? And what disk label do you have. Should be all caps and only letters & numbers, best with no spaces and not too long. FAT has lots of limits where NTFS has fewer but still some limits.

---

