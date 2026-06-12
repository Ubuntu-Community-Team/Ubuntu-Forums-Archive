---
title: "Automated Backups"
date: 2011-02-28
forum: General Help
---

### Post by Ceiber Boy on 2011-02-28
I have to perform automated backup of a NAS (Network Attached Storage), the backup is onto an external USB HDD. the backups have to be incremental (only make copies of files if they have been modified without deleting the duplicates) and to leave behind files on the backup that has been removed from source.

Rsync
My first program was using the program rsync. this kept saying that files had been moved and or modified on the source when they had not. 

sudo mount -t cifs //192.168.1.xxx/data /mnt/data -o user=xxxxx
rsync -r -d -v -c --progress /mnt/data /media/truecrypt1
sudo umount /mnt/data

cp
so i decided to go with the copy 'cp' command instead, using this code:
sudo mount -t cifs //192.168.1.xxx/data /mnt/data -o user=xxxxx
cp -u -r -v -f /mnt/xxxxx /media/truecrypt1
sudo umount /mnt/data

now there are three file i backup in this mannor, the first is 0.5GB the secong is 12GB and the third is 250GB. the two smaller files backup without issue, but the larger file continues to give problems with backing up certain files which i know have not been modified.

Questions
which is the best method to use (rsync or cp) and which switches do i need to achieve my specification? I've read through the man pages and think i have selected the correct ones!

If anyone has experience of using these programs on large files please respond as im am in need of any assistance you can offer, I'm also sorry i can be more explicit at this time as the exact messages are not the computer of writing this post, but i do remember the some of the files it had said had been modified or moved were PDF and JPG (if that's of any relevance)

---

### Post by TechWiz2100 on 2011-02-28
I had a similar thing going on a server I had running a while ago where I was developing with PHP. I ended up making a bash script that ran on CRON that created a new directory and backed up all the modified files and folder into that new folder but I can't seem to find the script. I'll post back if I find it but it was basically a combination of diff and cp.

---

