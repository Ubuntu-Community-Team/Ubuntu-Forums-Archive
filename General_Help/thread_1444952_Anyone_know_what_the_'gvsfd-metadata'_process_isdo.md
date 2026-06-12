---
title: "Anyone know what the 'gvsfd-metadata' process is/does?"
date: 2010-04-02
forum: General Help
---

### Post by cAlpha on 2010-04-02
I've been leaking memory like crazy of late and it all seems to be related to some kind of collection process labeled 'gvsfd-metadata' within System Monitor.  

In the recent past, loss of disk space related to difficulties playing a DVD seemed to be related to this process--its entry on the 'Processes' tab within the System Monitor showed it as using the largest percentage of CPU.  

Also, just a minute ago while watching a lengthy video on YouTube, I noticed that my root disk space was dropping by ~100M every couple of minutes again, while CPU usage was ramped up and 'gvsfd-metadata' was the primary cause.  

Anyone familiar with this or the process and know how to avoid bleeding memory?

---

### Post by lisati on 2010-04-02
It's quite common when watching videos on sites like YouTube for disk space to seem to disappear. This is because the viewer downloads the video and puts in the /tmp folder while/before displaying it. It should be cleaned out the next time you reboot.

Sorry, I don't know anything about gvsfd-metadata.

---

### Post by irishbreakfast on 2010-04-02
gvsf - gnome virtual file system.  stuff that handles samba, ntfs disks and other virutal filesystems/features.

"Unix file system extensions in the GNOME environment"  ( [http://www.usenix.org/publications/library/proceedings/usenix2000/freenix/full_papers/perazzoli/perazzoli.pdf](http://www.usenix.org/publications/library/proceedings/usenix2000/freenix/full_papers/perazzoli/perazzoli.pdf) ) might have further info

---

### Post by akakingess on 2010-04-02
I don't think this will help, but I have been using this computer and online and all for hours, and that process is currently 'sleeping' , do I don't know, does yours constantly stay awake or do you sometimes check and it's asleep?

---

### Post by irishbreakfast on 2010-04-02
I rarely have issues that cause me to use system monitor. Since gvfs is for virtual file systems, where is your /tmp (based on lisati's input)? Are you doing anything else that might be using something like ntfs, samba etc?

(akakingess, looks like I put an emoticon in before by accident)

---

### Post by akakingess on 2010-04-02
I can say that I use SAMBA and NTFS3G? (forgot the spelling for that), but either way I use both almost constantly as this computer kind of stores everything for the family via SAMBA and an extra NTFS drive (always mounted), so I don't know why mine is 'sleeping', but everything works.

---

### Post by irishbreakfast on 2010-04-02
Processes sleep when there is nothing for them to do at the moment or something more important needs attention. Even my torrent daemon which is running right now is sleeping quite a lot.
It seems like your machine has the external drive attached? But where is your /tmp directory? Which drive is it on?
If /tmp is on the ntfs drive, then gvfs would be busy handling the download. Plus, if another computer on your net was wanting to use the ntfs drive at the same time then it would very busy indeed, handling requests from both machines.
If /tmp is on your internal drive, then it seems gvfs shouldn't be so busy as it wouldn't be involved. That points again to the other machines (or yours) wanting to use that disk at the same time.
And then you need to consider the effects of the swapping going on between the downloading process and gvfs.
I hope that makes some sense - I should be in bed.

---

### Post by akakingess on 2010-04-02
I understand what you are saying, and I just hope that nobody thinks I am trying to solve anything, just supplying some more input in the hopes of finding out where the OPs memory leak is coming from, you are correct that nobody else in the house is accessing that NTFS drive, and my /tmp and /var are on the internal, I do have an NTFS shared drive from one of the windows machines mounted here, but not currently accessing or copying to/from it, so I should figure it would be asleep. As I stated, I just want to help the OP with the memory leak, because that used to be near the top of my list of things I hated about Windows boxes (all the dang memory leaks!  :)

---

