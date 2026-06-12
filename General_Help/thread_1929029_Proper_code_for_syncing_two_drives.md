---
title: "Proper code for syncing two drives"
date: 2012-02-21
forum: General Help
---

### Post by rmcellig on 2012-02-21
I have an external USB  HFS+ drive that has over 900GB of data that I would like to sync with another same size external USB NTFS formatted drive.

I am using Gnome schedule to enter the code for synching. What is the proper code to use so that my NTFS drive is always identical to the HFS+ drive?

---

### Post by SlugSlug on 2012-02-21
sudo rsync -a /path/to/source /path/to/dest

---

### Post by rmcellig on 2012-02-21
It doesn't seem to be working. What am I doing wrong? It seems as though I always have to manually execute the code for it to work. At least in Gnome schedule. I am trying this test to see if it works before I actually implement the code for my two USB drives.

---

### Post by gebri on 2012-02-21
you have to run it in reverse direction also, or look at
```
man rsync
```
for best accuracy ;)

---

### Post by rmcellig on 2012-02-21
Do you mean like this?

sudo rsync -a /home/randy/Desktop/test2/ //home/randy/Desktop/test1/

---

### Post by SlugSlug on 2012-02-21
depends what your doing ?

if you are saving all files on one drive ad just want the other as a clone then what u had 1st if fine.  If you want to save on both drives and have them sync togeather then u need 2 rsyncs 


first one then first one again but reversed

sudo rsync -a /path/one /path/two
sudo rsync -a /path/two /path/one

---

### Post by rmcellig on 2012-02-21
Basically, drive 1 is my main drive and drive two is the drive I want to clone to. I am testing it now with a couple of folders just to see if it works. So my test involves synching folder1  (the main folder), to folder2 (the cloned folder). Did I have it right originally? Should I be using the GUI app grsync? Just wondering. Thanks for all the help I am getting. I really appreciate this!!!

---

### Post by rmcellig on 2012-02-21
Would I be better off synching the drives or backing up the one drive to another?

---

### Post by SlugSlug on 2012-02-21
with900gig i'd rsync as it logs what its done already

---

### Post by rmcellig on 2012-02-23
This is the code I am using in Scheduled tasks. All I want is for the code to activate every minute so that I am sure that folder two is being updated every minute seamlessly behind the scene without any intervention on my part. This does not seem to be working at all and I don't know why.

All I want is folder two to always be identical to folder one. If I can get this to work so that folder two is updated every minute, I will be happy. I use Gnome scheduled tasks for other jobs I run involving the arecord tool which works flawlessly.


sudo rsync -a /home/randy/Desktop/folder1/  /home/randy/Desktop/folder2

---

### Post by SlugSlug on 2012-02-24
try without sudo asit may needyour pass if not using roots crontab

---

### Post by dcstar on 2012-02-24
> **rmcellig said:**
> I have an external USB  HFS+ drive that has over 900GB of data that I would like to sync with another same size external USB NTFS formatted drive.

I am using Gnome schedule to enter the code for synching. What is the proper code to use so that my NTFS drive is always identical to the HFS+ drive?

You **cannot** sync various filesystems to non-Linux filesystems like NTFS.

NTFS is not compatible with a multitude of Linux requirements, and I suspect HFS+ comes under this category.

---

### Post by Lars Noodén on 2012-02-24
> **dcstar said:**
> You **cannot** sync various filesystems to non-Linux filesystems like NTFS.

NTFS is not compatible with a multitude of Linux requirements, and I suspect HFS+ comes under this category.

HFS+ works fine under GNU/Linux and will preserve permissions and other file attributes.  

NTFS, though as you point out, is a lost cause and IMHO should not be used for anything.  A work-around for backing up onto NTFS would be to use [tar](http://manpages.ubuntu.com/manpages/oneiric/en/man1/tar.1.html).  However, the major drawback to that is that it will be slow because each backup will have to copy everything again even if it hasn't changed since last backup.  Best recommendation would be to either get rid of the NTFS partition or else resize it and split off a chunk to use as EXT4 or HFS+ for your backup.

---

