---
title: "Low hanging fruit question"
date: 2009-11-25
forum: General Help
---

### Post by bones12 on 2009-11-25
This should be an easy question but I haven't done it before. Can I mount a new hard drive to a mount point that isn't the usual /mnt/someDirectory or /media/MyFolder ?

I would like to mount a new hard drive to something like /MyPublicDirectory.

Of course I have a reason for it. Samba sees the directory now on my primary drive. I'm outgrowing my one drive server and would like to move all of my files off to the new drive but let Samba be none the wiser. Of course I will have to move my files all around and so forth. But the questions is... Is there something sacred about /mnt or /media?

Would be happy to hear if anyone has done that

---

### Post by jacobs444 on 2009-11-25
absolutely you very well can!

---

### Post by jacobs444 on 2009-11-25
My extra drive is mounted to /home/username/storage1

---

### Post by jacobs444 on 2009-11-25
Absolutely nothing sacred about those directories, just a default for the OS

---

### Post by scouser73 on 2009-11-25
Please follow the instructions set out in this tutorial for mounting drives: [[COLOR="Red"]**Mount Hard Drives**[/COLOR]]("https://help.ubuntu.com/community/Mount/")

---

### Post by jacobs444 on 2009-11-25
Just make sure you have the correct permissions, and mount it where you want it. Just don't put it under a specific system folder like /var /usr /boot etc

simple question, simple answer.

---

### Post by bones12 on 2009-11-25
Thanks for all of the good suggestions. Especially about the permissions and systems folders even though I wasn't about to mount in those folders it's still good information to know. 

I thought it was possible but I didn't want to move several gigs of data and get things all hosed up without at least asking a few simple questions.

---

