---
title: "Ubuntu 10.10 freezing up solid"
date: 2011-02-09
forum: General Help
---

### Post by scorey1609 on 2011-02-09
Hey y'all,

I'm a bit perplexed on this issue.  I searched through Google looking for similar issues and can't seem to find one that quite fits and I was wondering if someone else has heard of this happening.

I recently installed Ubuntu 10.10 (32 bit) on a friend's Dell Inspiron 1501 to replace the entirely screwed up Windows Vista that was on it.  The install process went without flaw or issue.  Everything worked perfectly out of the box.  My issue comes when I try to copy files from my terabyte external onto the computer (the files she had backed up from her vista install).  Files larger than about 300MB cause the computer to freeze up solid.  The only thing that works is the power button to force shutdown.  There's no mouse... nothing.  This made me think there was a hardware issue but...

The external drive has no issues on any computer other than this one so I'm inclined to think the Dell is causing the issues.  I ran Ubuntu's drive test and it reported no errors, and MemTest 86 comes up with no errors.

So, I'm looking for some educated guesses.  If Ubuntu can handle installs and lengthy updates with no problem, but then connecting an external USB HDD and copying over files causes it to freeze up tighter than I've ever seen Ubuntu freeze before...  could a faulty USB port cause this? Motherboard? Ubuntu itself?  I'm installing Ubuntu from CD.

What do you think?

Thanks,

Corey

---

### Post by jeebustrain on 2011-02-09
Have you tried just letting it sit for a while? I occasionally see issues pushing 5GB+ at a time (large files) to my NAS. The whole GUI will freeze up, but eventually when the copy finishes, it's fine.

I've done some reading and while someone more knowledgeable might chime in, I believe it has something to do with CPU I/O scheduling issues with the kernel.

---

### Post by scorey1609 on 2011-02-09
Hey,

Yes, I've let it sit for several hours and the computer never regains consciousness.

Thanks,

C

---

### Post by coffee412 on 2011-02-09
> **scorey1609 said:**
> Hey,

Yes, I've let it sit for several hours and the computer never regains consciousness.

Thanks,

C

Hi, 

Might help if we setup for debugging a bit. Before you go to copy the large file open a term window and type in "sudo tail -f /var/log/messages" without qoutes. This will show all messages in realtime. Then start the copy and see if you get any related messages.

Worth a shot if you ask me.

coffee

---

### Post by DrReaper on 2011-02-09
Copy any other file on to the USB drive at near the same size and see if it works or fails. It may be the file your trying to copy.

---

### Post by scorey1609 on 2011-02-09
yeah, definitely.  Thanks.  Do I have to copy the files from bash?  or can I just drag and drop?

---

### Post by scorey1609 on 2011-02-09
Hey DrReaper,

I've frozen this thing up with probably over 50 files each requiring a hard reboot to continue copying these files up.  Each time I semi-solved the problem by just copying one picture/song/document at a time, but that doesn't fix the problem and it isn't worth copying 20 gigs of files one at a time.

Thanks, though.  Usually, that would be a good point!

---

