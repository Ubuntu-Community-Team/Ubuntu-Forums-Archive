---
title: "Disk error check"
date: 2010-05-11
forum: General Help
---

### Post by londonlad on 2010-05-11
hi all,

every 4 or 5 times i boot up, i get the purple screen & it says it running HDD checks to see if there are any errors, sometimes it works ok, & sometimes the screen goes blank, i then have to restart..............is all of this normal?

---

### Post by dondiego2 on 2010-05-11
I just got that today.  I let it run, left for a while, came back and the sign in screen was up so I figured everything was OK.  I just upgraded to 10.04 a few days ago so I'll have to wait and see if it happens again.

---

### Post by dcstar on 2010-05-11
> **londonlad said:**
> hi all,

every 4 or 5 times i boot up, i get the purple screen & it says it running HDD checks to see if there are any errors, sometimes it works ok, & sometimes the screen goes blank, i then have to restart..............is all of this normal?

You should **never** just "restart", this is an almost guaranteed way to corrupt your system and/or lose data.

Allow the system time to do whatever it is doing, or switch to a text console to properly shut the system down if you suspect that it is not working correctly.

---

### Post by RTrev on 2010-05-11
The odd thing is that fsck runs like lightning on ext4 file systems.  I'm not sure why it takes so long during boot.

I'm inclined to check manually every now and then, until the whole Plymouth (Edsel? :)) thing gets sorted out.

---

### Post by londonlad on 2010-05-12
oh, checking from 0 - 70% is really fast, but from 70 - 100% takes about 10-15mins! :(
And, how do i manually start a disk error check?

---

### Post by RTrev on 2010-05-12
> **londonlad said:**
> oh, checking from 0 - 70% is really fast, but from 70 - 100% takes about 10-15mins! :(
And, how do i manually start a disk error check?

Unmount the disk in question, then:

```
sudo fsck /dev/sd...
```

e.g.:

```
sudo fsck /dev/sdc1
```

On my 500G drives, it's done before I can get my finger off the Enter key.

---

