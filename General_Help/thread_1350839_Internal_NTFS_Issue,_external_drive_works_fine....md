---
title: "Internal NTFS Issue, external drive works fine..."
date: 2009-12-09
forum: General Help
---

### Post by bristolbadger23 on 2009-12-09
I'm having a total headache with this machine... this is a dual boot XP/Jaunty box. XP has a documents drive on which i save all my data and want to be able to see that from Jaunty.

Upon loading Jaunty the disk is evident and I can even browse through and was once able to make and Rsync of 70G worth of music to a USB drive. Literally nothing changed, and then i couldn't....

Essentially what happens is I click on the Icon for everything, (the NTFS drive) i have a look around maybe open a doc, copy it or do nothing, simply cd /media/everything, or in the GUI, moving into the drive crashes the whole system. I have about 45 seconds between accessing the drive and the whole thing just hanging. I then have to power off to get it going again.

Any ideas how to troublshoot this?

Between this and not being able to get my wireless card to work i am seriously thinking of giving up and using headless FreeBSD when i need to and settling for Microsoft XP as a desktop. Computing shouldn't be this difficulty, and so far the last 4 days have been taken over by one or other of these woes...

---

### Post by llamabr on 2009-12-09
Hi, there.  I like freebsd too, and use it for a headless server.

I'm not quite clear on how you're accessing the other partition (it's a local partition, right?).

Try installing:

```
sudo apt-get install ntfs-config
```

and run it from a terminal.

it comes with a gui which is nice for beginners.

---

