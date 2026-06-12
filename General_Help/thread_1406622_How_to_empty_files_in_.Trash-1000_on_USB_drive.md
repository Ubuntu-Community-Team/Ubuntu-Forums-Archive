---
title: "How to empty files in .Trash-1000 on USB drive?"
date: 2010-02-14
forum: General Help
---

### Post by oxf on 2010-02-14
Apologies if this has been asked before, which I'm sure it has from what I see googling around, but I cant understand this fully.

I have a piles of files in the .Trash-1000 folder on my flash drive that I want to delete. I can see them if I go in as root using the command line and entering "gksu nautilus" but it still wont allow me to delete them.

Please can some one tell me how to delete them and better still remove that folder?

Thanks..:)

---

### Post by fooman on 2010-02-14
with mine,  i just right-click on the .Trash-1000 file and choose "move to trash" (no need to be root)

i then get a message saying that i "cannot move file to trash,  do you want to delete immediately?" ....click "delete" and they are gone.  :)

---

### Post by oxf on 2010-02-14
> **fooman said:**
> with mine,  i just right-click on the .Trash-1000 file and choose "move to trash" (no need to be root)

i then get a message saying that i "cannot move file to trash,  do you want to delete immediately?" ....click "delete" and they are gone.  :)

Hi,

That doesnt work for me! If I right click on the folder the "move to deleted items folder" is grayed out. But I can highlight the folder and hit delete, then tells me "cant  send to trash..do you want to delete permanently?" I try to do that and says it "cant delete becuase of an error"

---

### Post by jocko on 2010-02-14
Just go to your normal trash and empty it. That will remove all ".Trash-1000" folders on any currently mounted file system.

---

### Post by fooman on 2010-02-14
what happens if you just highlight the .Trash-1000 folder...then press the ctrl + h keys?

---

### Post by drs305 on 2010-02-14
Do you also get the error using "gksu nautilus" if you highlight the trash folder and use SHIFT-DEL? Needing "gksu" may be necessary if you have any root trash hanging about. Using just the delete key can send the trash right back into the trash bin so nothing is actually accomplished, although it shouldn't produce an error message.

If this is an NTFS format, was the device cleanly unmounted the last time it was used? Are you having any problems with the other files on the device? You might want to mount and unmount it in Windows if the error persists.

---

### Post by oxf on 2010-02-14
> **fooman said:**
> what happens if you just highlight the .Trash-1000 folder...then press the ctrl + h keys?

Well that deletes it but as soon as I remount the flash its back again complete will all the files inside!

@drs305...
Using shift delete in root nautilus doesnt seem to do anything! yes its formated in FAT32. 

Whats so confusing and frustrating about all this from googling around is that there seems no consistant way of removing them. I'm beginning to think it might be easier to just reformat the drive but would like to understand it as it will probably come up again in the future..

---

### Post by joeknoodle on 2010-02-14
I usually just unmount the volume, and it then asks if I want to empty the trash. Kludgy maybe, but it works for me.

---

### Post by jocko on 2010-02-14
Have you tried what I said yet?
.Trash-1000 is just the normal users trash, so it will be removed when you empty your trash.

Ctrl+H just switches between showing and not showing hidden files in nautilus, so that doesn't do anything.
Trying to send it to the trash will not do anything, since you can't send the trash to itself.
But you can always shift+delete (=really delete, not just try to move it to the trash).

---

### Post by oxf on 2010-02-14
> **joeknoodle said:**
> I usually just unmount the volume, and it then asks if I want to empty the trash. Kludgy maybe, but it works for me.

Nice idea but... Same problem they are back again next time the drives mounted!

---

### Post by oxf on 2010-02-14
> **jocko said:**
> Have you tried what I said yet?
.Trash-1000 is just the normal users trash, so it will be removed when you empty your trash.
Ctrl+H just switches between showing and not showing hidden files in nautilus, so that doesn't do anything.
Trying to send it to the trash will not do anything, since you can't send the trash to itself.

Sorry forgot to comment on that :) 
If I go the normal wastebasket and the files are there. But when I try to delete them (after asking me if I want to) nothing happens!

shift+delete might work for the future but doesnt remove whats already there though!

---

### Post by SuperSonic4 on 2010-02-14
```
rm -rf /media/disk/.Trash-1000/*
```

Where /media/disk is the path to your flash drive

---

### Post by oxf on 2010-02-14
> **SuperSonic4 said:**
> ```
rm -rf /media/disk/.Trash-1000/*
```Where /media/disk is the path to your flash drive

Hmmm? this seems to be a permissions thing, even when under root. 
When I enter the above it returns "cannot remove... read only file system" and a couple of "input/output errors" too. But...  I do own them and  cant seem to change the ownership either:confused:

---

### Post by jocko on 2010-02-14
> **oxf said:**
> Sorry forgot to comment on that :) 
If I go the normal wastebasket and the files are there. But when I try to delete them (after asking me if I want to) nothing happens!
Sounds like a permission problem then.
Can you write files to the usb drive?
Can you delete files with shift+delete (from the .Trash-1000 folder or anywhere else)?

Have you checked the file system for errors?

---

### Post by oxf on 2010-02-14
> **jocko said:**
> Sounds like a permission problem then.
Can you write files to the usb drive?
Can you delete files with shift+delete (from the .Trash-1000 folder or anywhere else)?

Have you checked the file system for errors?


I can write to the USB

I cant delete with shift+delete from .Trash-1000. Says "read only" but cant change permissions either.

Havent had time to check for errors yet..

Thanks!

---

### Post by jocko on 2010-02-14
> **oxf said:**
> Hmmm? this seems to be a permissions thing, even when under root. 
When I enter the above it returns "cannot remove... read only file system" and a couple of "input/output errors" too. But...  I do own them and  cant seem to change the ownership either:confused:

> **oxf said:**
> I can write to the USB

I cant delete with shift+delete from .Trash-1000. Says "read only" but cant change permissions either.

Havent had time to check for errors yet..

Thanks!

Definitely seems like a file system or actual hardware problem if you can write to the disk, but not even root can delete.
Open up a terminal and:
```
sudo umount /media/[COLOR=Blue]disk[/COLOR]
sudo fsck -favVr /dev/[COLOR=Red]sdb1[/COLOR]
```(change [COLOR=Blue]disk[/COLOR] and [COLOR=Red]sdb1[/COLOR] in those commands to whatever [COLOR=Blue]mount point[/COLOR] and [COLOR=Red]device node[/COLOR] the drive really has)

---

### Post by oxf on 2010-02-14
> **jocko said:**
> Definitely seems like a file system or actual hardware problem if you can write to the disk, but not even root can delete.
Open up a terminal and:
```
sudo umount /media/[COLOR=Blue]disk[/COLOR]
sudo fsck -favVr /dev/[COLOR=Red]sdb1[/COLOR]
```(change [COLOR=Blue]disk[/COLOR] and [COLOR=Red]sdb1[/COLOR] in those commands to whatever [COLOR=Blue]mount point[/COLOR] and [COLOR=Red]device node[/COLOR] the drive really has)

Hmm...

mbdb@M2000:~$ sudo umount /media/NEW\ VOLUME
mbdb@M2000:~$ sudo fsck -favVr /dev/sdb1
fsck from util-linux-ng 2.16
[/sbin/fsck.vfat (1) -- /dev/sdb1] fsck.vfat -favr /dev/sdb1 
dosfsck 3.0.3 (18 May 2009)
dosfsck 3.0.3, 18 May 2009, FAT32, LFN
Checking we can access the last sector of the filesystem
Boot sector contents:
System ID "MSDOS5.0"
Media byte 0xf8 (hard disk)
       512 bytes per logical sector
      4096 bytes per cluster
        32 reserved sectors
First FAT starts at byte 16384 (sector 32)
         2 FATs, 32 bit entries
   1001472 bytes per FAT (= 1956 sectors)
Root directory start at cluster 2 (arbitrary size)
Data area starts at byte 2019328 (sector 3944)
    250333 data clusters (1025363968 bytes)
63 sectors/track, 255 heads
        63 hidden sectors
   2006610 sectors total
FATs differ but appear to be intact. Use which FAT ?
1) Use first FAT
2) Use second FAT

---

### Post by jocko on 2010-02-14
> **oxf said:**
> Hmm...

FATs differ but appear to be intact. Use which FAT ?
1) Use first FAT
2) Use second FAT
If you have anything important on the drive, maybe you should consider backing it up before you continue (ctrl+c exits fsck)...
I can't really help you with what to answer to that question. If you have backed up the important files from the drive, just pick one option and let it find the next error...
But then again, if you have it backed up already it's probably better to delete the entire partition and reformat the drive...

---

### Post by oxf on 2010-02-14
> **jocko said:**
> If you have anything important on the drive, maybe you should consider backing it up before you continue (ctrl+c exits fsck)...
I can't really help you with what to answer to that question. If you have backed up the important files from the drive, just pick one option and let it find the next error...
But then again, if you have it backed up already it's probably better to delete the entire partition and reformat the drive...

Yes I'll back up and then reformat. I cant help thinking though this was caused by me using the drive in both Windows PC's at work and Linux? 
Anyway thanks for your help! :)

---

### Post by oxf on 2010-02-14
Well I did the obvious backups and did continued with the disk check.

What I found was this. on both the "FATS" there were a substantial number of "unconnected clusters" which it offered to repair. It's a moot point now since I'll just reformat the driveWhat I'm wondering is if since it was originally formated as FAT32 and has been too and forth between my Ubuntu and other Windows PCs this was what lead to my original problem? espacially since this has happened on more than one USB drive?

Any opinions?

---

### Post by john.quinn on 2010-07-11
What finally worked for me was simply cutting the .Trash-1000 folder from the removable drive and pasting it into my home folder on the local hard drive. Then I was able to "Move to Trash", and finally "Empty Trash". I verified that when I removed the drive and remounted it, .Trash-1000 was gone.

---

### Post by GreenishBlob on 2011-10-23
if you also have a windows pc just throw it into theyre and delete works easly :P

---

### Post by oldos2er on 2011-10-23
Closed. Please don't bump old threads.

---

