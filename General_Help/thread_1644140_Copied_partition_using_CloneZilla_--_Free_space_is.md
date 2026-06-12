---
title: "Copied partition using CloneZilla -- Free space is reported incorrectly"
date: 2010-12-12
forum: General Help
---

### Post by algernon83 on 2010-12-12
I recently upgraded to a bigger hard disk. I used CloneZilla to copy my 150GB ext3 /home partition on my Ubuntu system to a shiny new 800GB ext3 /home partition. However, I've filled it up to almost 150GB, and I keep getting warnings that I have only 300MB available. It looks like the free space is being reported incorrectly. GParted recognizes the size of the partition as 800GB, and Nautilus reports the same when I boot from a live CD. I've tried using tune2fs to remove the reserved blocks and e2fsck -f to fix any errors, but nothing's changed. Can anyone please make a suggestion?

---

### Post by Quackers on 2010-12-12
I'm afraid I don't have a link for you, but when you move a Linux file system to a bigger disk there is a way of making it recognise the new disk size. You resize the file system to fill the space. It's something to do with "resize2fs", do a search maybe on the forum, or Google it.

---

### Post by Quackers on 2010-12-12
Try post #2 in this thread. Obviously the actual command may be different for your drive

[http://ubuntuforums.org/showthread.php?t=1242394&highlight=resize2fs](http://ubuntuforums.org/showthread.php?t=1242394&highlight=resize2fs)

---

### Post by algernon83 on 2010-12-12
That was it! Thanks, Quackers; you're my new best friend!

---

### Post by Quackers on 2010-12-12
Very nice :-)

---

