---
title: "How can I tell if data corruption occured after an unclean shutdown (ext4)?"
date: 2011-03-20
forum: General Help
---

### Post by andrei_1 on 2011-03-20
After an unclean shutdown I started the Live CD and did a fsck -fv on the root partition. It told me about a few (~10) "orphaned inodes" that had to be cleared and that the file system was modified.

Now, I don't think this information is very useful to me. Maybe those orphaned inodes were innocuous temporary files used by some script currently running. But then again, maybe some very important file got utterly corrupted (I don't even know the low level details of ext4 to even ascertain what might happen in such a situation).

Ultimately, I don't even care if corruption DID occur, but I do want to know WHAT got corrupted so that I can restore the files from my backups (I always backup everything offsite).

To make a long story short: can I somehow find out WHAT files might have been affected by possible corruption issues? Please do tell if you have any kind of information that might clear the confusion I'm currently in.

Thanks!

---

### Post by abyrne on 2011-03-20
From my experience, ext4 is a pretty stable filesystem. Power outages have happened often to my home server. But every time I boot back up, the system is fine. Unless you notice something while using Ubuntu (random freezing, file transfer errors, etc.), then everything is probably OK.

---

### Post by jerome1232 on 2011-03-20
If any file fragments were found fsck will put them under lost+found on the root of the drive, in my experience because of the file-system damage fsck doesn't even know what they are, sometimes you can look in lost+found and figure out "oh hey that's my /etc/blah/blah configuration file" but most likely if anything is there it will be junk.

---

### Post by andrei_1 on 2011-03-20
> **jerome1232 said:**
> If any file fragments were found fsck will put them under lost+found on the root of the drive, in my experience because of the file-system damage fsck doesn't even know what they are, sometimes you can look in lost+found and figure out "oh hey that's my /etc/blah/blah configuration file" but most likely if anything is there it will be junk.

Does Ubuntu clear the /lost+found dir on each reboot perhaps? Or maybe fsck does that after a clean run (when no issues are found)? I'm asking because the dir is currently empty even though I did see the message about "orphaned inodes" a couple of days ago...

---

### Post by jerome1232 on 2011-03-20
AFAIK it doesn't ever clean it out, most likely the fix didn't cause any data loss or it couldn't recognize anything to move to lost+found.

---

### Post by andrei_1 on 2011-03-20
> **jerome1232 said:**
> AFAIK it doesn't ever clean it out, most likely the fix didn't cause any data loss or it couldn't recognize anything to move to lost+found.

Oh, so either it was really nothing, or it was something very serious :P. This is just what I was saying... I hate this uncertainty.

Isn't ext4 supposed to be a *journaling* file system? I can't believe there are no tools that can tell me what files might have been affected.

I have also encrypted my entire root partition which might be an additional risk factor for possible corruption.

I understand ext4 is very reliable, but this is not reassuring to me if in 1 out of 1000 cases it might corrupt a very important file... So that's why I'd trade reliability for certainty.

---

### Post by andrei_1 on 2011-03-26
> **jerome1232 said:**
> AFAIK it doesn't ever clean it out, most likely the fix didn't cause any data loss or it couldn't recognize anything to move to lost+found.

I ended up writing a Python script that will md5sum all the files in the system. I'm running this under SCHED_IDLE and "ionice -c3" every 2 hours. This script will only process the files that have their mtime changed.

Another script is for diff purposes that will show me what files have changed, got deleted, created etc. I also have an ignore file to ignore certain directories that are not important and that are likely to have frequent changes.

I'm running the diff script after an unsafe shutdown or if I have any reason to believe data corruption could have occured.

Yes, I'm that paranoid :P

---

