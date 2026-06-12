---
title: "Unstable filesystem problems?"
date: 2009-11-24
forum: General Help
---

### Post by Ck.asdf on 2009-11-24
I originally posted my question in the security forum because my intent was to get my data after Ubuntu stopped working (& my home directory was encrypted).  However, someone suggested I run fsck which fixed whatever the problem was and allowed me to boot back into Linux.

Things were fine for a day, then tonight Firefox locked up (stopped responding, faded to black).

I waited around for a little bit (couple minutes) to see if it would come back, but it didn't, so I eventually decided to log off.  That wasn't working quite like it should, as it dropped me to a console, so I just typed sudo reboot, then got my original problem - some kind of problem with the filesystem which caused it to not want to boot.
Ran "fsck -C /dev/sda3 -y" and I'm back ... but I'm worried that it isn't going to last.

Is there anything I can do to find out what might be causing this instability?
A few notes:

I'm using ext4 file system
Ubuntu 9.10 x86 32bit
hardware details in my signature

I'm attempting to use this as a sort of hobbyist audio production machine (as well as standard user things such as Firefox, etc), and as a result I have Jack audio on here. I also have pulseAudio because I can't seem to get rid of it.

One thing I just remembered is both times I've had this problem, I've been playing music from Aqualung - to be specific, MP3s from an NTFS partition.
The first time the problem occurred, I was using Jack to power the audio for Aqualung, the second time (tonight) I was just using pulseAudio, since Jack didn't seem to want to start (it claimed something else was using hw0).

The only two things I had running tonight were Firefox & Aqualung.

Any suggestions?


For further notes of what's been going on, please check this thread:
[http://ubuntuforums.org/showthread.php?p=8376585](http://ubuntuforums.org/showthread.php?p=8376585)

---

### Post by Ck.asdf on 2010-01-26
Hey, this happened to me again recently.  I'll try in just a little bit to run the command I mentioned, but what do you think I might try to get it to remain more reliable?

---

