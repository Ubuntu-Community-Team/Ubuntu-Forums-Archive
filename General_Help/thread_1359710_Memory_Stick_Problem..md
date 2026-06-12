---
title: "Memory Stick Problem."
date: 2009-12-20
forum: General Help
---

### Post by Sourmiloko on 2009-12-20
Hi, so... I was downloading pictures onto a usb flash dive/SD memory sick (its called a MicroSD HC) and everything was going fine untill I downloaded a pic and it said there was no more room on the drive. So I backed up all the files (videos/music ext) onto the desktop and then tried to move the pics back over, but it is now telling me that there is no room on the disk  when there are no files on it. I go into property's and it can't get the usage information. I am looking for a way to format it, but i dont know how. Please help!

---

### Post by lukeiamyourfather on 2009-12-20
I'd use GParted, I think its installed by default in the administration menu but I can't remember for sure. Make sure to select the correct device in the top right menu, then you can remove, create, and do whatever with partitions and file systems. If that doesn't do it, its possible the flash on the SD card is bad and you'll have to get a new SD card. They usually last long enough for their capacity to become obsolete before they die, but sometimes they die prematurely from faults or if used for heavy IO loads (since they have relatively few write cycles). Cheers!

---

### Post by Lukas666 on 2009-12-20
> **Sourmiloko said:**
> Hi, so... I was downloading pictures onto a usb flash dive/SD memory sick (its called a MicroSD HC) and everything was going fine untill I downloaded a pic and it said there was no more room on the drive. So I backed up all the files (videos/music ext) onto the desktop and then tried to move the pics back over, but it is now telling me that there is no room on the disk  when there are no files on it. I go into property's and it can't get the usage information. I am looking for a way to format it, but i dont know how. Please help!

First try this:

sudo fsck -r /dev/sdXX

where sdXX is your drive name

---

### Post by Sourmiloko on 2009-12-20
I had to go into Synaptic but it worked! Thank you sooo much!

---

### Post by blackened on 2009-12-20
The trash bin can act weird on removable drives sometimes. If you deleted the files after copying them to the desktop, then they are probably still in the drive's trashcan.

Instead of formatting, try this: open the drive in nautilus, then click "View" -> "Show Hidden Files". After that, delete the now-visible trash file and you should regain all the space you were missing.

---

