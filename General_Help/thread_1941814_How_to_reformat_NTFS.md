---
title: "How to reformat NTFS"
date: 2012-03-16
forum: General Help
---

### Post by bikeman01 on 2012-03-16
Hi

Title of this tread doesn't really say it all so here goes:

Until yesterday my Dell Inspiron was happily running Windows 7, then it wouldn't boot with the message 'NTLDR is missing' - funning I thought Win7 didn't use NTLDR, maybe it was required becaus eth laptop was orig Vista, who knows.

Anyway I tried everything I could think of; 
WIndows recovery - no restore points, 
Window repair - didn't work,  
Restore my Arcronis Trueimage backup - no Harddisk found.
Used a Win98 CD to recreate the MBR
Tried to reinstall from Win7 cd - no dice as no os installed.

It was looking like the HD had failed. So I stuck in a Ubuntu cd and started up. The HD hadn't failed and I could see all the partitions including the Dell recovery partition.

In desperation, I installed Ubuntu, reformatting the entire hd as EXT3 in the process. Works fine but I really need to get window reinstalled.

Now that the HD is formatted EXT3 I can't restore from anything or re-install windows - Acronis cant see teh HD and Windows says the HD format is incompatible.

**Are my windows partitions recoverable?**

I figure if I can use the Ubuntu cd to reformat NTFS I would be able to reinstall. Please can someone tell me how move back from Ubuntu to windows. 

**How can I reformat my harddisk fron EXT3 to NTFS.**

Thanks

---

### Post by sudodus on 2012-03-16
Are you prepared to overwrite the whole HDD or do you need some files from the old ntfs partition? If so, are you prepared to do some work to get them back before reformatting?

You can try to recover your files from the file content using ***Photorec***. This will work only if you have not overwritten the actual data of the files. I'm not sure what happened during the reformatting. Unfortunately the files written when installing Ubuntu might have overwritten the files you would be looking for.

*I think* you can reformat the partition to NTFS with ***gparted*** in a live session started from your Ubuntu install disk.

---

### Post by Mark Phelps on 2012-03-16
Neither Vista nor Win7 use NTLDR; that is used by XP.

If you're really trying to get Win7 working again, strongly suggest you go to a Win7 forum: sevenforums.com

They have threads and tutorials dealing with such problems.

---

### Post by buddyd16 on 2012-03-16
> **bikeman01 said:**
> 
In desperation, I installed Ubuntu, reformatting the entire hd as EXT3 in the process. Works fine but I really need to get window reinstalled.

Now that the HD is formatted EXT3 I can't restore from anything or re-install windows - Acronis cant see teh HD and Windows says the HD format is incompatible.

If I am reading that correctly then it sounds like you wiped out your windows and recovery partitions in which case depending on how the format of the drive was performed it is highly likely that you have lost any data that was stored in the windows and recover partitions.

Reinstalling windows at this point should only require that you boot from the windows disk and run through its install procedure. If you do not have a windows disk, most manufacturers have dumped providing the disk in favor of the recover partition, then I suggest you contact your PC manufacturer and see if they can send you an OEM disk which usually costs between $10-$25 in my experience.

---

