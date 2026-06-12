---
title: "Have Ubuntu installed on an external..."
date: 2011-05-30
forum: General Help
---

### Post by World Domination on 2011-05-30
I have Ubuntu installed on an external HDD, so my laptop would dual boot Win7/Ubuntu. I used WUBI to do it.
My USB on my external HDD broke, so I took apart my external HDD and found I was able to attach it internally to one of my desktops. I hook it to this desktop and I am able to boot into Ubuntu, but  I have a ton of files on the partition that Ubuntu is *not* installed on that I won't to pull off. How would I go about doing this?

tl;dr:
I have files on my non-Ubuntu partition I want to access while on Ubuntu.

---

### Post by linuxinstalledfromhdd on 2011-05-30
You would need to mount that to do a data migration.  I don't know specifically in your situation since you have a very, shall we say, unique configuration. But if you wait long enough -maybe- someone knows.  

BUMP

---

### Post by World Domination on 2011-05-30
> **linuxinstalledfromhdd said:**
> You would need to mount that to do a data migration.  I don't know specifically in your situation since you have a very, shall we say, unique configuration. But if you wait long enough -maybe- someone knows.  

BUMP
I was initially told I couldn't Install Ubuntu on an external and boot from it, while using it as a secondary storage in Windows, but I managed to do it. (Obviously).
Hope someone has an answer for me, the last back up I have of this particular drive is nearly 6 months old.

---

### Post by linuxinstalledfromhdd on 2011-05-30
You can do it. And you can do it much easier than the way you did it.  Honestly, you can take any external drive and turn it into a NAS box file server, and then you don't have issues about data migration later on. Check it out after you get this resolved, because it would have saved you some time.:P

---

### Post by World Domination on 2011-05-30
> **linuxinstalledfromhdd said:**
> You can do it. And you can do it much easier than the way you did it.  Honestly, you can take any external drive and turn it into a NAS box file server, and then you don't have issues about data migration later on. Check it out after you get this resolved, because it would have saved you some time.:P
Will do, Thank you for the suggestion!

---

### Post by linuxinstalledfromhdd on 2011-05-30
I will bump your thread later on tonight when the after hours late night crew arrives.  Although it is a holiday for most of the free world so it might wait until tomarrow.  Just so you know my friend. 

Cheers :)

---

### Post by World Domination on 2011-05-31
Ok, I want to add a bit more information about my situation.

I used to have my external hooked to my laptop. My laptops internal HDD booted win7, while my external booted Ubuntu. My other partition on the external is just random files (like pictures, text documents, etc, no OS).

My externals USB port broke, and my computer would no longer read the external. SO I took it apart hoping to find a fix. I realized I could hook up my external inside my desktop as an internal HDD and boot up Ubuntu off it, meaning it is my primary (only) HDD in this computer. However my problem is I cannot get the other partition with the random files to mount.

---

### Post by oldfred on 2011-05-31
Can you use a liveCD? What format is the partition you want to mount? Is it just the NTFS partition that wubi is installed into?

Does partition not mount because it may need a filecheck like e2fsck?

I do not know wubi, but saved some commands. You should be able to see the windows partition as host?

How-to: Recover files from Wubi install with LiveCD
[http://neosmart.net/forums/showthread.php?t=5004](http://neosmart.net/forums/showthread.php?t=5004)
[Script] Mount Wubi Disk from Linux mount old wubi in new install
mount ntfs partition first:
[http://ubuntuforums.org/showthread.php?t=1037874](http://ubuntuforums.org/showthread.php?t=1037874)
mkdir /mnt/windows
mount -o loop /mnt/windows/ubuntu/disks/root.disk /mnt/ubuntu

If you need to run fsck on wubi:
sudo mkdir /media/win
sudo mount /dev/sda1 /media/win
sudo fsck /media/win/ubuntu/disks/root.disk
Then check if you can mount it & read it:
sudo mount -o loop /media/win/ubuntu/disks/root.disk /mnt

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

