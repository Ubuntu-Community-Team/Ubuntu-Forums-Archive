---
title: "clamav won't work"
date: 2009-08-05
forum: General Help
---

### Post by theozzlives on 2009-08-05
I don't know if it's a problem with clamav, the fact that I'm using an Alpha of Karmic, or that I have ext4. When I run:
```
clamscan -ri --move=/tmp/virus /home/ozzie
```
I get:
> LibClamAV Error: Can't load /var/lib/clamav//main.cvd: Can't verify database integrity
ERROR: Can't verify database integrity

----------- SCAN SUMMARY -----------
Known viruses: 62888
Engine version: 0.95.2
Scanned directories: 0
Scanned files: 0
Infected files: 0
Data scanned: 0.00 MB
Data read: 0.00 MB (ratio 0.00:1)
Time: 0.310 sec (0 m 0 s)


I ran freshclam and it seemed to update fine, but it still don't work. Any ideas?

---

### Post by fennec_fox on 2009-08-05
I've never seen that before. Did the permissions get changed on the main.cvd file so you can't read it and does the file actually exist? 

A reinstall of clamav is the only thing that comes to mind.

Sorry, wish I could be of more help.

---

### Post by theozzlives on 2009-08-05
> **fennec_fox said:**
> I've never seen that before. Did the permissions get changed on the main.cvd file so you can't read it and does the file actually exist? 

A reinstall of clamav is the only thing that comes to mind.

Sorry, wish I could be of more help.

A closer look at the path in the error shows 2 frontslahes before main.cvd:

> /var/lib/clamav//main.cvd

I wonder if that's why it can't find it, it's there I checked. Well with Alpha software you expect such inconveniences.

---

### Post by fennec_fox on 2009-08-05
I didn't even notice that the first time I read it. It's suppose to be /var/lib/clamav/main.cvd

Not sure how you'd fix that.

---

### Post by NoBugs! on 2010-02-14
I have the same problem on fully up-to-date system. I had this problem before, I remember fixing it by removing some clam scan packages and reinstalling them, but now the problem is back.

---

