---
title: "USB drive appears as read-only"
date: 2010-03-06
forum: General Help
---

### Post by bigred1 on 2010-03-06
I have a Coby MP3 player  which functions as a USB drive. It has always worked fine, both on Ubuntu Karmic and on the Windows (booted from another disk).

Now, in Ubuntu, it appears as read-only (but it works fine when I boot into Windows on the same machine). How can I deal with this? It's not a matter of my fstab, which I have never manually edited; the USB device is always auto-detected.

---

### Post by dcstar on 2010-03-06
> **bigred1 said:**
> I have a Coby MP3 player  which functions as a USB drive. It has always worked find, both on Ubuntu Karmic and on the Windows (booted from another disk).

Now, in Ubuntu, it appears as read-only. How can I deal with this? It's not a matter of my fstab, which I have never manually edited; the USB device is always auto-detected.

Unmount it and then do a fsck on it.

---

### Post by bigred1 on 2010-03-08
Thanks, I did that and got the following session. However, the USB drive (i.e., the Coby MP3 player) is still read-only. This is strange, given that it worked as read/write on this OS until recently, and still works on Windows. Any ideas on what has changed or on how I can make it read/write?

I noted [this]("http://ubuntuforums.org/showthread.php?t=685996") item. I certainly can't reformat since this MP3 player contains more that just storage.

```

sudo fsck /dev/sdc1
fsck from util-linux-ng 2.16
dosfsck 3.0.3, 18 May 2009, FAT32, LFN
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  65:01/00
1) Copy original to backup
2) Copy backup to original
3) No action
? 3
FATs differ but appear to be intact. Use which FAT ?
1) Use first FAT
2) Use second FAT
? 1
/.Trash-1000
  Contains a free cluster (184704). Assuming EOF.
Reclaimed 21179 unused clusters (86749184 bytes).
Free cluster summary wrong (821809 vs. really 720705)
1) Correct
2) Don't correct
? 1
Leaving file system unchanged.
/dev/sdc1: 287 files, 284172/1004877 clusters

```

---

### Post by bigred1 on 2010-03-08
@dcstar: Thanks! The solution was Windows chkdsk: I plugged  in the USB drive after the grub2 screen but before choosing Windows as my OS, then let chkdsk run. Alternately I could have, within Windows, set chkdsk to run on the next reboot. 

Maybe fsck could have done it, but if so, it required some other parameters or responses in the interactive session.

I think that using this USB drive back-and-forth between Windows and Ubuntu caused the corruption, since some of the corrupt files were in **.Trash** . Also, another USB drive, this one a thumb-drive, was corrupted with similar errors noticed in **.Trash**

By the way, do you know if an MP3 player still works after reformatting--i.e., is the software separate from the flash disk?

---

### Post by schtufbox on 2010-05-17
> **bigred1 said:**
> @dcstar: Thanks! The solution was Windows chkdsk: I plugged  in the USB drive after the grub2 screen but before choosing Windows as my OS, then let chkdsk run. Alternately I could have, within Windows, set chkdsk to run on the next reboot. 

A forum search found this, helped me too, as the memory card in my wm6.1 phone connected via wm5torage (turns it into a usb drive) had suddenly become read only :(  I had to plug it into my mrs' laptop and fdisk /f  the card...works fine now!

> **bigred1 said:**
> Maybe fsck could have done it, but if so, it required some other parameters or responses in the interactive session.
I tried, but it didn't seem to help, sadly.

---

