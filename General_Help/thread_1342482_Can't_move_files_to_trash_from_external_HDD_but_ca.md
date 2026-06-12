---
title: "Can't move files to trash from external HDD but can be deleted permanantly"
date: 2009-11-30
forum: General Help
---

### Post by woolgatherer on 2009-11-30
Hi people! I'm using Ubuntu 9.04-64 bit. I got a problem with deleting files form my external hard disk. When I right click on a file or a folder and move it to trash from external HDD it won't go to trash but would give an error message " Cannot move file to trash, do you want to delete it immediately?". When I select yes it would get deleted. Even when I delete using delete button same stuff occurs. But I want files to be moved to trash before I delete them permanantly. Help Please!

---

### Post by kristine12 on 2009-11-30
The reason is your External HDD don't have its own trash can. The only way to move your files from your HDD to trash is to drag and drop it to the trash can. That is why some USB drives have their folder named RECYCLER or .Trash-1000. This folders serve as the trash can of the disk.   :p

---------------------------------------------------------------------------------------------------------
My First Problem Answered! ^_^

---

### Post by woolgatherer on 2009-11-30
Thanks for the quick reply! You mean to say that in no way I can achieve "right click -> move to trash" . I tried making .Trash1000 and again "move to trash" won't work. You mentioned "dragging and dropping" but that is not a comfortable option :) - that would be like creating a backup folder and deleting later. Btw my ext HDD is **partioned**(*fat32 format*) - has this anything to do with my problem 'cause I see that I can move to trash from a flash drive.

---

### Post by kristine12 on 2009-12-01
Creating a .Trash-1000 folder on your HDD will absolutely not work because those kind of folder are built-in on the drives. What I'm trying to tell you is that there are drives that have their own trash can while others don't have.

---

### Post by kristine12 on 2009-12-01
Your HDD partition with fat32 format don't have an effect to the other drives.

---

### Post by jbrown96 on 2009-12-01
The problem here is your file system. There is no support for trash in fat32. The work-around is to create a hidden folder like kristine12 said. Ubuntu doesn't do this because fat32 isn't a native file system. Unfortunately, there isn't a good way around this. 

Switching to a linux file system, ext3/4, would be the best option. However, I have a feeling that you would like to use this in Windows as well. You could try changing it to ntfs (windows default fs). There may be support for trash in ubuntu with ntfs.

---

### Post by woolgatherer on 2009-12-01
Hmm! Then in this case I would like to add that my flash drive 4gb is also fat 32 and "move to trash" works well with it. Even my internal HDD has got fat32 partitions and "move to trash" works intimately with those too. Btw the external HDD am using is a seagate freeagent model with 1 TB capacity.

---

### Post by woolgatherer on 2009-12-07
Hi friends! I apologise for indicating that my ext HDD is of fat32 system. Today, after installing gparted I found out  that the file system in my external HDD is **NTFS**  and not fat32 and I guess what jbrown indicated is true except that fat32 is supported and NTFS is not. Thanks Kristine! Thanks Jbrown! :p

---

### Post by woolgatherer on 2010-01-21
Hi again ppl FYI, I've upgraded to karmic Koala and to my utter surprise this problem doesn't persist anymore whatever be the partition type!

---

