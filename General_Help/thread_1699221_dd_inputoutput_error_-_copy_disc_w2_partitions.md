---
title: "dd input/output error - copy disc w/2 partitions"
date: 2011-03-03
forum: General Help
---

### Post by elj4176 on 2011-03-03
I was given a CD for work purposes and when I put the disc into the drive I get 2 disc icons on my desktop. One has data (a pdf file) and the other has serveral audio tracks. 

I tried to use dd to image the disc but it gives an input/output error immediately without copying anything. If I try to use brasero or k3b to copy the disc it only copies the audio portion. The data portion does not show up in the drop down to copy - only the audio.

If I right-click the data (or audio) desktop icon and select 'copy' from the shortcut menu then it creates an image of the audio portion. 

for dd i tried:
dd if=/dev/cdrom of=/home/username/test.iso
This give an immediate error with no data written to the iso file.

dd if=/dev/cdrom of=/home/username/test.iso bs=2M conv=notrunc,noerror
This copies a small amount of data to an iso file but it wasn't usable.

any input would be appreciated.

---

### Post by TeoBigusGeekus on 2011-03-03
Could the cd be damaged?

---

### Post by aeiah on 2011-03-03
what does your /dev/ look like? if you had a hard drive (called /dev/sda) with two partitions you'd see /dev/sda (the drive), /dev/sda1 and /dev/sda2 (the two partitions). is anything like that appearing for your cdrom?

also, i get ```

[main ~] ls -al /dev/cdrom
lrwxrwxrwx 1 root root 3 2011-03-03 16:07 /dev/cdrom -> sr0

```

try doing dd if=/dev/sr0 instead of /dev/cdrom

---

### Post by elj4176 on 2011-03-03
cd is not damaged. It will play audio when inserted on a windows machine but if you explore the cd it will show the pdf file. 
The audio files play fine in linux and I can open the pdf as well.

I was seeing /dev/sr0 and /dev/sr1 as well as /dev/cdrom /dev/cdrom1 

I tried all of them but /dev/sr0 and /dev/cdrom0 seemed to be the audio CD portion of the disk. I couldn't access the other /devs

I finally got it to work by switching to Roxio in windows and using the 'backup' function to create a .gi file (general image) and then burn that file with Roxio.

Still want to know why it wouldn't work with dd (or k3b or brasero) for that matter. Here is what ls -al /dev/cdrom shows:

user@user:~$ ls -al /dev/cdrom
lrwxrwxrwx 1 root root 3 2011-03-03 12:07 /dev/cdrom -> sr0
user@user:~$ ls -al /dev/cdrom1
lrwxrwxrwx 1 root root 3 2011-03-03 11:33 /dev/cdrom1 -> sr1

---

