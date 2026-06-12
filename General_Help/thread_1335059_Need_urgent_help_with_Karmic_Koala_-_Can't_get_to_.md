---
title: "Need urgent help with Karmic Koala - Can't get to desktop"
date: 2009-11-23
forum: General Help
---

### Post by Cyber-Meth on 2009-11-23
I've been cruising around the internet and forums to see if anyone else had this specific problem, but it seems not. 

Basically, Ubuntu is just crashing when i try to log in. I get to the back and fourth scroll loader and eventually it just stops scrolling and hangs there forever. I can't get to my desktop, which is highly inconvenient at this point. Right now i'm having to access the internet with a live CD, so any help would be appreciated. 
This only started happening today, and if it's any help, i had a massive bundle of updates yesterday.

---

### Post by fancypiper on 2009-11-23
It sounds as if the system might be doing an fsck.  While in the live cd, I would fsck all my Linux partitions except for swap.

---

### Post by prshah on 2009-11-23
> **Cyber-Meth said:**
> 
Basically, Ubuntu is just crashing when i try to log in. I get to the back and fourth scroll loader and eventually it just stops scrolling and hangs there forever.

> **fancypiper said:**
> It sounds as if the system might be doing an fdisk.  While in the live cd, I would fdisk all my Linux partitions except for swap.

I think fancy piper means "fsck" not "fdisk". Please do not use fdisk, you can end up destroying your partitions.

When (or just before) the scrolling hangs, can you press Ctrl+Alt+F8 and post back the last lines seen?

Please boot into recovery mode, choose "root shell" and give the command```
touch /forcefsck
```; then press Ctrl-Alt-Del to restart the system. This will force a diskcheck, as suggested by fancypiper.

Did the updates complete successfully? Please boot into recovery mode, choose root shell and run ```
sudo apt-get check
```

If none of these suggestions help, can you please try to post the log file /var/log/messages.1 ? If you need more details on how to access this log file, please post back.

Some actions (especially fsck) can damage your files or data, so you do this at your own risk.

---

### Post by fancypiper on 2009-11-23
> **prshah said:**
> 
Some actions (especially fsck) can damage your files or data, so you do this at your own risk.Uh... did you mean especially fdisk? :confused:

---

### Post by prshah on 2009-11-23
> **fancypiper said:**
> did you mean especially fdisk? 

Nope I mean fsck; however I do not mean to exclude fdisk; both are capable of damage to files/data. The chances are remote, though.

---

### Post by fancypiper on 2009-11-23
I have only lost data when I was doing a backup and had a power failure, but I don't blame it on fsck.  It looked as if lost&found had some partial files that were being copied, so I just chose fix and I never could tell that I had actually lost any data.  I just assumed it was an awaiting write or one in progress when the power quit.

I did recover data once using fdisk, though.  I happened to have the numbers for the partition boundaries I had previously used written down, I set them as they were before, mounted and there was a ton of data that I thought I had lost.

Try that in Microsoft Windows!

---

