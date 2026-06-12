---
title: "Ubuntu / Windows 7 - strange NTFS issue"
date: 2012-01-03
forum: General Help
---

### Post by Tralce on 2012-01-03
Before I describe my problem, I think it would be wise to describe my setup. I have a desktop running Ubuntu 11.10 only, and a laptop dual-booted with Ubuntu 11.10 and Windows 7. The laptop has a 640GB hard drive with the majority being given to the Windows 7 partition, and Ubuntu only has, well, less than 50GB anyway. I have all the pertinent directories in my Ubuntu home dir (Documents, Music, etc.) mount-bound to their corresponding directories in my Windows 7 user dir. For example, in fstab (I'm in Windows right now so I don't have access to the fstab to copy and paste from) /home/tralce/Documents is bound to /media/Windows7/Users/Tralce/Documents and the files are stored in the Windows partition. Altogether it's around 100GB of data over probably 100,000 files. I use Unison under Ubuntu to mirror these pertinent home dirs on the laptop with their desktop counterparts. For years this has worked wonderfully.

Here's where it gets weird: Every now and again, and much more frequently lately, files... well, they change. I keep my home dir well sorted, with text files under Documents, and videos under Videos. But, here's an example, I went to open a small file in ~/Documents, called packages, which contained a short list of packages I like to install on a fresh Ubuntu installation, and it had turned into a copy of Fellowship of the Ring. The movie. On both the laptop and the desktop, and in both Windows and Linux. It was still just called packages. 

This happens a lot, and I'm losing valuable files this way. 

Under Windows I've run chkdsk /f c: and that sometimes corrects a few files but even that is starting to fail. Also sometimes a plaintext file will suddenly turn into an empty directory of the same name. 

Help please...

---

### Post by topsites on 2012-01-03
I am going to venture a guess that one or more of your data storage units has become corrupted, the more convoluted your file-management system is (or has become) the finer the chance of this happening somewhere along the way.

At this point, more than likely I would start by backing up EVERYTHING important onto some brand new media.
Writeable DVD's hold quite a bit of data, for example, but I'd definitely be thinking in terms of a back up of some sort.
The reason I like writeable discs (CD's / DVD's) is because once written it is much more difficult for data to become corrupted.

> **Tralce said:**
> For years this has worked wonderfully.

Yup, yup.

Where have I heard that before...

You can not...
As a rule, simply transfer files between Linux and Windows and synchronization and back and forth just like that.
Technically, it should work.

For myself I use an 8GB USB drive for those files that I do wish to share but like yourself, sometimes some thing gets the hiccups.

The part that caught my attention...
If my install requires a 100GB of files then I'm giving it a 100+GB partition (and not, no offense, 50GB with smoke and mirrors)
Especially if you have 640GB's I'd give Linux the room it needs, 150!
Maybe even 200...

You know, there might be a way you can re-partition without losing a file or maybe run some virus / spyware tests as well
but ultimately I think you are going to have to simplify your file management system.

Hope that helps

---

### Post by Tralce on 2012-01-03
> **topsites said:**
> I am going to venture a guess that one or more of your data storage units has become corrupted, the more convoluted your file-management system is (or has become) the finer the chance of this happening somewhere along the way.



Yup, yup.

Where have I heard that before...

You can not...
As a rule, simply transfer files between Linux and Windows and synchronization and back and forth just like that.
Technically, it should work.

For myself I use an 8GB USB drive for those files that I do wish to share but like yourself, sometimes some thing gets the hiccups.

The part that caught my attention...
If my install requires a 100GB of files then I'm giving it a 100+GB partition (and not, no offense, 50GB with smoke and mirrors)
Especially if you have 640GB's I'd give Linux the room it needs, 150!
Maybe even 200...

You know, there might be a way you can re-partition without losing a file or maybe run some virus / spyware tests as well
but ultimately I think you are going to have to simplify your file management system.

Hope that helps

The reason Linux has such a small partition is that there's nothing stored in it except the OS and a few packages. It's actually only using 4.7GB right now. 

My file management system is convoluted because I need to be able to access these files under both Windows and Linux and to the best of my knowledge there's no such thing as a stable ext4 file system driver for Windows 7. How can I still access all these files on both OSes without my so-called smoke and mirrors technique?

---

