---
title: "Kubuntu Lucid - CDRom won't mount"
date: 2010-06-28
forum: General Help
---

### Post by dlrocket89 on 2010-06-28
Hi all,

I've been using Ubuntu for about a year now, when I upgraded to 10.4 LTS I switched over to Kubuntu to give KDE a try.  Overall, I like it, except that when I try to load up files off of the DVDs I burned as data backup, the DVDs won't auto mount.  

I've tried 5 different data DVDs (burned with Brasero in Ubuntu 9.04) and a blank DVD.  Nothing mounts.

Someone please help...while helping, assume I know nothing other than how to open a terminal and navigate the K Menu.  Thank you very very much in advance!!!

Dustin

---

### Post by cariboo on 2010-06-28
Can you manually mount a dvd? At the prompt in a terminal type:

```
sudo mkdir /media/cdrom
```

then mount the cdrom:

```
sudo mount /dev/sr0 /media/cdrom
```

---

### Post by dlrocket89 on 2010-06-28
> **cariboo907 said:**
> Can you manually mount a dvd? At the prompt in a terminal type:

```
sudo mkdir /media/cdrom
```then mount the cdrom:

```
sudo mount /dev/sr0 /media/cdrom
```



Comes back as 

mount: /dev/sr0: unknown device



I only have 1 DVD/CD drive on this machine.

---

### Post by Ole Juul on 2010-06-29
> Comes back as
mount: /dev/sr0: unknown device

I have the same problem with Lucid, and both the separate CD and DVD drives don't automount. When I try to mount the CD I get the same message as you. However, if I type:
```
sudo mount -t iso9660 /dev/sr0 /media/cdrom
```
Then the drive will mount. Unfortunately I haven't been able to unmount it. I think there is a bug in Lucid.

Anyway, in your case you need to use sr0 and whatever file type a DVD is. I'll be watching this thread. :)

---

### Post by dlrocket89 on 2010-06-29
> **Ole Juul said:**
> I have the same problem with Lucid, and both the separate CD and DVD drives don't automount. When I try to mount the CD I get the same message as you. However, if I type:
```
sudo mount -t iso9660 /dev/sr0 /media/cdrom
```Then the drive will mount. Unfortunately I haven't been able to unmount it. I think there is a bug in Lucid.

Anyway, in your case you need to use sr0 and whatever file type a DVD is. I'll be watching this thread. :)


Tried that, I get a message about "media not found at sr0"

---

### Post by dlrocket89 on 2010-06-29
I have a dead desktop with a different DVD drive on it, should I swipe that I try putting that in?

---

### Post by Ole Juul on 2010-06-29
> **dlrocket89 said:**
> I have a dead desktop with a different DVD drive on it, should I swipe that I try putting that in?
If you think the present drive works, or used to work, then switching drives is probably a waste of time. I say that because it looks like the drive is recognized. Automounting is different issue.

In my case, the computer with the problem is running Lucid server with a Fluxbox WM so the problem is not with KDE or Gnome either. :) I'm pretty sure the problem lies with the basic system which deals with mounting and/or automounting. In another thread on this forum, someone claimed that the problem was in the 2.6.32-22 kernel and could be solved by compiling a 2.6.34 one.

---

### Post by dlrocket89 on 2010-06-29
> **Ole Juul said:**
> If you think the present drive works, or used to work, then switching drives is probably a waste of time. I say that because it looks like the drive is recognized. Automounting is different issue.

In my case, the computer with the problem is running Lucid server with a Fluxbox WM so the problem is not with KDE or Gnome either. :) I'm pretty sure the problem lies with the basic system which deals with mounting and/or automounting. In another thread on this forum, someone claimed that the problem was in the 2.6.32-22 kernel and could be solved by compiling a 2.6.34 one.


I know the drive works, it's the drive I installed Kubuntu off of.

Hrm...I'd like to avoid needing to do something of that level if I can, I'll wait and see if someone chimes in here...

---

### Post by dlrocket89 on 2010-06-29
OK, here's a question.  The drive worked fine to install Kubuntu off of the install disk, now it doesn't work (now that the system is on its own).

Is there a way to install the CDROM driver that's used during the install process?  That one works fine.

---

### Post by dlrocket89 on 2010-06-29
SOLVED

Based off of another thread that I found, I starting messing around in the BIOS, related to the CDROM drive.  I forgot exactly what I changed, it went from "auto" to "large"...I think it had something to do with formatting.  In any case, it works now, mounts right up automatically.

Like I say, there was someone else who solved it this way too, so if you're having the problem (and it sounds like there's quite a few of us, trying changing the BIOS settings, as it deals with the CDROM drive only.  Took a couple of iterations, but it worked.

---

### Post by Ole Juul on 2010-06-30
Congratulations!

I was going to suggest that you try typing "lshw" to confirm that the drive is recognized but assumed it was since it worked with another installation. Changing the bios when changing version seems a bit odd to me. Oh well, as long as it works now. :)

In my case, I'm on top of the hardware and can mount drives from the command line. I'm still looking for an automount solution.

---

