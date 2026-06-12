---
title: "Restore directory tree after disk problems"
date: 2009-10-07
forum: General Help
---

### Post by DeBOBAHer on 2009-10-07
Hello!
I have the IDE hard drive where there are a lot of JPEG files (about 50'000 or more). They were cataloged in several folders and had file names that help to find them. There** file names are very important** for me.
This files were used as network samba drive in windows network. Last sunday there were power problems and computer with this disk were anormaly shot down. And then automatically start up. After this i was reported that some files aren't at there places. So wait for the end of the day and try to check the disk with the **fsck.ext3** *remote using the ssh*.
It said me that file system is mounted and it is not safe to check the disk but i check it any way. During the check there were a lot of errors like
```
Block bitmap for group X is not in group (block Y) 
Relocate<y>? 
```**I press Y key **and let fsck make its work. After that i was unable to do anything in ssh - server didn't found commands. I decided that it would be better to don't do anything else to not destroy the data. That happened at the monday evening.And at the tuesday i was reported that some image files wasn't acceptable via network.
I decided that it is good idea to unmount the partition and check it again. But umount wasn't found on server. And ls to... I try to reboot the computer. The boot wasn't complete. Root partition can't mount.
```
mount: wrong fs type, bad option, bad superblock
```I take this disk from that computer and plug into my desktop. Errors on mount was the same. So i try to fsck this partition from my computer and it shows me the same errors as before. **And i let it relocate everything.**
After that i start to "googling" the problem. And make the image of partition with **dd**. So** before that i make all movements on real hard disk.**
Now i have an image that didn't mount. Even if i mount with "-b [another superblock copy position]". If i fsck the disk with  "-b [another superblock copy position]" i can relocate that errors and after that i will taking mountable image with clear root with only "lost+found" folder that looks like contains all my files. But **they are having different filenames than original files**. So i can't use them.
If i view an image before fsck (F3 in mc) i can find there lists of files in folders that i need. So i think that information about folders are still there but i can't get it out of there.
I know that it was my fault but i realy need that files.
Is there possibility to extract them from the image with the debugfs or something like that if i will found correct positions of folders inonds? I can find them with viewer looking for the filenames and them looking back to find the start of file list but i not sure how many byte before file list are still in this inode.
Ma&#1091;by there is another way of extracting files with there originally filenames?
Help me please.

---

### Post by oldos2er on 2009-10-07
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

No guarantee that it will restore the original file names tho'.

---

### Post by DeBOBAHer on 2009-10-07
Thanks, oldos2er!

I try'd to use testdisk but it didn't help me.

---

### Post by Slim Odds on 2009-10-07
You're not going to like to hear it.... but backups are the only real answer to this question.

---

### Post by Baelus on 2009-10-07
Here's some info on the lost+found folder:

[http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/lostfound.html]("http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/lostfound.html")

Recovering the filenames is probably not possible. :(

---

### Post by DeBOBAHer on 2009-10-08
Thank you!
Actually i thought that i have an RAID with mirror there. But it wasn't work like i seen after the break. Now i recover data from the backup. But it is very old. So i still try to recover that files that are on failure partition. As i writes before i can find some of the file names in raw image. So i will be looking for the possibility to recover them. I think that debugfs could help me with it. But this will take a lot of time.
If i will do that i will write here about the algorithm of recovery.

---

### Post by DeBOBAHer on 2009-10-26
Well, looks like i found the solution. I use R-Studio (*program*) for restoring the files. It doesn't ideal, but it works. I think that i have many links to same files. Because *program* shows to me a lot of files with similar names (this are the files i need and i know that they can't be in several copies). Directory structure can't be repaired such way. So i will need more steps to repair everything but i could get the files (that what i already did). To recover files i was need to select not all of them but the ones with "normal" size (above the 1 KB and below the 9 MB - my files are JPEGs with small resolution). And another step is filtering restored files because some of them are incorrect (have damaged content and didn't show anything).
For this filtering i will try to use imagemagick. If it wouldn't help me than i will write my own script to delete all non image files (by there content).

---

