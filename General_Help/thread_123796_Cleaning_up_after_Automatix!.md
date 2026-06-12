---
title: "Cleaning up after Automatix!"
date: 2006-01-31
forum: General Help
---

### Post by gravediggers on 2006-01-31
Was just wondering what all I need to do to clean up ater running automatix, and for that matter, after any major package upgrade. My Ubuntu box has only 6GB disk with about2.5GB for / (the rest is swap and /home). After running automatix, df -k shows 0 kB available on /. What do I need to do to remove old pakages and generally clean up?

---

### Post by jazzgossen on 2006-01-31
Synaptic is a good way to clean up packages (you can find it inder system/administration). Look through the lists and mark all that you don't want anymore.

---

### Post by gravediggers on 2006-01-31
OK

Partially got the system back!:) 
Of course, Synaptic is absolutely useless if you have zero disk space because X won't fire up. However, I started a failsafe terminal session and did *apt-get clean* and about 168MB available in /.
I have 2 questions:
What else do I need to do to clean up after running Automatix?
How can I safely increase the size of my / partition and also create another partition for /var?

---

### Post by newuser111 on 2006-01-31
try deborphan

sudo apt-get install deborphan


then run sudo dpkg --purge $(deborphan)

keep doing it until it doesnt remove anything

---

### Post by gravediggers on 2006-01-31
[QUOTE=newuser111]try deborphan[/QUOTE]
thx - it removed some crap that didn't install properly with automatix (stuff to do with gstreamer and lame codecs,etc - will have to get manually later), but my 2 questions still remain!

---

