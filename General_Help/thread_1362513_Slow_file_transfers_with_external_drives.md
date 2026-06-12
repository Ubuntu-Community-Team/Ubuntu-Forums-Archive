---
title: "Slow file transfers with external drives"
date: 2009-12-23
forum: General Help
---

### Post by anonSam on 2009-12-23
I have a problem with slow transfer rates to and from external drives. When moving or copying files it starts out normal for about 10 seconds, then suddenly pauses, then begins again a few seconds later transferring about 1.5mb every 6 seconds (It transfers, pauses, transfers, pauses). It always finishes but obviously takes forever for larger files. I've done a lot of searching and only tried this: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/66115/comments/5](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/66115/comments/5) but it didn't work. I have 3 external drives and it now does this on 2 of them but they were not always this way. I'm running Karmic 32 bit AMD/ Kernel 2.6.31-16-generic / GNOME 2.28.1 and the external drives are USB / NTFS. Any ideas?

---

### Post by anonSam on 2009-12-27
Any new ideas? bump

---

### Post by diablo75 on 2009-12-27
Exactly what kind of hard drives are we talking about here?  Flash USB sticks are typically slow when writing data, but can be read much faster by comparison.  If it's an actual external hard drive... you should be able to write to the drive at 10 MB per second or more (on USB2)...

---

### Post by anonSam on 2009-12-27
One is a 750GB Western Digital My Book and the other is a 750GB Maxtor OneTouch (external storage/hard drives). I don't how to tell what USB version it is for sure but I think it's 2.0. Normally they would max out at 32MB (but usually average around 24MB). Not only do they go extremely slow now, they have these strange 6 second pauses between a 'burst' of data transfer. It's painful to watch. Those 2 drives transfers are slow no matter what drive I move files to or from. I have a another external drive connected with Fire Wire and it has never had this problem. From the searches I've done it seems like it's some USB2 bug, but no one's really figured it out yet and the bug reports are closed due to lack of information. I'm willing to try any suggested work around.

---

### Post by StuartN on 2009-12-27
> **anonSam said:**
> From the searches I've done it seems like it's some USB2 bug, but no one's really figured it out yet and the bug reports are closed due to lack of information. I'm willing to try any suggested work around.

It seems like Ubuntu Karmic introduced (or certainly made much worse) some kind of timing error that causes USB 2 speeds to fall back. If you look in dmesg then you will likely see some error / warning messages. It seems worst with USB flash memory products, or maybe there are more varieties of them. If you search on the message text you will find plenty of suggestions, but it doesn't look like any have great success.

---

