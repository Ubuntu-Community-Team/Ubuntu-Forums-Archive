---
title: "Gparted crashed while moving partition!!"
date: 2011-02-28
forum: General Help
---

### Post by diegoocampo on 2011-02-28
So I was moving and resizing a ntfs partition and i just touched gparted window and it crashed!! it was about 66% of finishing the operation... Now i guess i have a big mess in my hard drive and i dont know how to start solving it! i am in a ubuntu live cd and waiting for your help, any ideas??

If i open gparted now it shows the same partition table than before resizing and moving.. so i guess now part of my data is in this unallocated space after the sda5 partition..

thanks in advance!

[IMG]http://img571.imageshack.us/img571/1438/gpartedx.png[/IMG]

---

### Post by psusi on 2011-02-28
Time to restore from backup.

---

### Post by Quackers on 2011-02-28
Or try testdisk, maybe.
Does the Windows system still boot?
It is a good rule of thumb that Windows tools should be used to change Windows partitions and Linux tools used to change Linux partitions. It can be dangerous to mix the two.

---

### Post by Mark Phelps on 2011-02-28
So, what Windows OS are you running -- Win7? If so, try opening the Win7 Disk Management utility and see what it reports regarding the NTFS partitions.

If it still sees them, I would boot into Win7 (if you can) and try running chkdsk on the NTFS partitions.

HOWEVER, an alternative, if you want to experiment, would be to download a trial version of GetDataBack from Runtime Software, install it in Windows, run it, and see what it finds in the other NTFS partition.  If it finds all your files, you will have to buy it to do actual data recovery -- but you can try it for free.

As others have said, and my own experience confirms, Windows utilities tend to work better with NTFS volumes, Linux utilities tend to work better with Linux partitions.

---

### Post by diegoocampo on 2011-02-28
Thank you all for your answers! I will try with chkdisk in windows then.

I have windows 7 installed, and before doing that i wanna be sure (all my documents are in this partition!!) i was wondering-> even if windows recognizes the partition and try to fix it with chkdisk what about the data that is in this unallocated space?? this is the problem i see! gparted first move the data and then write the partition table with the partition expanded.. but i think windows will behave like if my ntfs partition is shorter than it really is!

should i proceed with chkdisk.. or maybe try with testdisk (how can i use it from live cd by the way?? 

This is what i get if i try to access to this partition under ubuntu->

"Error mounting: mount exited with exit code 13: ntfs_mst_post_read_fixup: magic: 0x95bd0503  size: 4096  usa_ofs: 39878  usa_count: 45845: Invalid argument
Actual VCN (0x640c3b7224ab4b8d) of index buffer is different from expected VCN (0x2).
Failed to mount '/dev/sda5': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details."

---

### Post by diegoocampo on 2011-02-28
I tried testdisk in the first place.. it makes deep sectors reading but i am afraid it doesn't fix the problem.. this unallocated space was a partition before.. and a partition that i removed and in where now must be part of the files from the ntsc partition.. but what testdisk find is this removed partition and try to write a new partition table with it. So i didn't let it do it.

What can i do?? maybe if i manually expand the ntsc partition, taking all this unallocated space and then run chkdisk /f to let it find the files and put them together again... don't know, just guessing..

any ideas please??

---

### Post by psusi on 2011-02-28
You can try photorec and pray, but like I said before, restore from backup.  A crash in the middle of moving a partition pretty much means your data are gone.

---

