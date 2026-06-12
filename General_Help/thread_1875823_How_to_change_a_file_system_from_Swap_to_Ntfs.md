---
title: "How to change a file system from Swap to Ntfs?"
date: 2011-11-05
forum: General Help
---

### Post by qwertykeyman on 2011-11-05
So I was trying to reinstall ubuntu on my 3rd hard drive but I accidently turned my 2ed drive (my windows ntfs storge) into a swap drive with only 1 click from the ubuntu installer, Now I want to turn it back to NTFS and hopefully keep all my data, but when I tried to edit the partition in the ubuntu disk utility ( i did successfully install ubuntu to the drive i wanted) I get "Error Modifying Partition" and the following error code.

Thanks for your help =)

Error modifying partition: helper exited with exit code 1: In part_change_partition: device_file=/dev/sdc, start=1048576, new_start=1048576, new_size=1000202241024, type=0x07
Entering MS-DOS parser (offset=0, size=1000204886016)
MSDOS_MAGIC found
looking at part 0 (offset 32256, size 1000202241024, type 0x07)
new part entry
looking at part 1 (offset 0, size 0, type 0x00)
new part entry
looking at part 2 (offset 0, size 0, type 0x00)
new part entry
looking at part 3 (offset 0, size 0, type 0x00)
new part entry
Exiting MS-DOS parser
MSDOS partition table detected
containing partition table scheme = 0
got it
got disk
got partition
new_size=1000202241024 but resulting size, 1000201224704, smaller than requested

and that last part goes on indefinatly and ends with the following

Error: Can't have a partition outside the disk!
changed partition to start=32256 size=1000202241024
committed to disk
ugh, offset or size changed
offset:     1048576
size:       1000202241024
new_offset: 32256
new_size:   1000202241024

---

### Post by BillyBoa on 2011-11-05
Did you try to see if you can recover your data, before trying something else, using a live CD?

---

### Post by killermist on 2011-11-05
From a live-cd terminal, using **cfdisk**, changing the partition type from swap back to ntfs should make the partition accessible as ntfs again (maybe after a reboot), *provided no writes were made to the partition while it was "swap" (including formatting as swap)*.  If anything was written as swap, the NTFS data may be corrupted and permanently lost.

---

### Post by qwertykeyman on 2011-11-05
> **BillyBoa said:**
> Did you try to see if you can recover your data, before trying something else, using a live CD?
How would I go about Recovering the data?

---

### Post by qwertykeyman on 2011-11-05
> **killermist said:**
> From a live-cd terminal, using **cfdisk**, changing the partition type from swap back to ntfs should make the partition accessible as ntfs again (maybe after a reboot), *provided no writes were made to the partition while it was "swap" (including formatting as swap)*.  If anything was written as swap, the NTFS data may be corrupted and permanently lost.

When I try to open cfdisk from a live CD I get "Fatal Error: Cannot open disk drive Press any key to exit cfdisk"

---

### Post by BillyBoa on 2011-11-05
Boot with a live CD and try to see if you can access your files on the hard drive.

---

### Post by qwertykeyman on 2011-11-05
I cant because the drive is now swap, this is exactly the problem im having

---

### Post by BillyBoa on 2011-11-05
In that case I'm afraid that you cannot do many things. Im sorry

---

### Post by oldos2er on 2011-11-05
When booted from the LiveCD, unmount swap in Gparted. Assuming you have internet access via the LiveCD, install testdisk to see if it can recover anything. ```
sudo apt-get install testdisk
```
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by qwertykeyman on 2011-11-06
When I try to "undelete" as the wiki states to do, it gives me "Can't Open Filesystem. Filesystem seems damaged...

am I just screwed?  *sigh*

---

### Post by oldfred on 2011-11-06
I have used photorec to retrieve lost data. It just scans a drive for anything that may look like a file and save it. I had saved a text file many times and it found all the old copies. Never was sure I found last saved version. It is a slow process, and you have to have a drive of the size to store all the recovered data. It does not recover file names but does extensions.

gddrescue, Scalpel, magic rescue, photorec, foremost, sleuthkit & others
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)

Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)

Use scripts to help sort files:
[http://www.cgsecurity.org/wiki/After_Using_PhotoRec](http://www.cgsecurity.org/wiki/After_Using_PhotoRec)
use flac tags to rename files 
[http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html](http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

---

### Post by qwertykeyman on 2011-11-06
Thank you very much, Ill try each of these and see if I have any luck

---

### Post by oldfred on 2011-11-06
You can try to change from swap to a type with this:

Backup partition table to text file & save to external device.
sudo sfdisk -d /dev/sda > PTsda.txt

Type 83 is Linux, if NTFS you want 7 and you have to change sdb7 to your drive & partition. Post PTsda.txt contents if you want.

change sdb7 to type 83
sudo sfdisk --change-id /dev/sdb 7 83

---

