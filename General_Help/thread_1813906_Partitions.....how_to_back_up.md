---
title: "Partitions.....how to back up"
date: 2011-07-28
forum: General Help
---

### Post by fidelandche on 2011-07-28
Hi all,
I am guessing the answer to this is going to be easy and I should know the answer but for the life of me I don't. So I did a fresh install of 11.04, I installed it along side Vista with the following partitions 90GB NTFS 53GB /home 2GB/Swap and 15GB/(Root) Now I have some file in my home folder and I would like to back them up to the 15GB partition, my question is how do I do this? and how do I find the partitions? 

Cheers

Andy

---

### Post by seawolf167 on 2011-07-28
/home -> / (root) backup... note that your home partition is bigger than your root partition! Anyways, the commands would be:

first create a folder in / for your backups

```
sudo mkdir /path/to/backup/folder
```then the easiest way IMO would be to use rsync

```
rsync -ruv /home/yourusername /path/to/backup/folder
```

I suggest a different approach - backup to an external drive formatted in ext4. There are a [number of methods ]("https://help.ubuntu.com/community/BackupYourSystem")you can use to do this. Additionally, you can use [Clonezilla ]("http://www.clonezilla.org")to image your entire disk to the external drive.

---

### Post by ajgreeny on 2011-07-28
Why do you want your backups to go to the root partition?  It does not seem a very good idea to me, and is certainly not the usual place to send backups of your system;  you will very soon run out of space.

The siting of, and therefore finding the folders in either / or /home is totally transparent to your filesystem, and when you look in nautilus there will be no indication of the different partitions involved;  everything will appear to be part of the total filesystem.

I strongly recommend you backup to some other, preferably external disk/partition, and keep away from the root partition entirely.

It is not a good idea to put files in / if you:-
a) are not sure what you are doing, and 
b) have a small partition as you do.

---

