---
title: "Home partition full (?)"
date: 2010-08-09
forum: General Help
---

### Post by maghoxfr on 2010-08-09
I keep getting a pop-up that says that I have a full home partition, according to it, I have only 110Mb free. But when I open Gparted I see much more free space on my home partition. Why is this? I attached a Gparted screenshot, it looks pretty messy, I know. 

Another question, what's the windows swap for? i'd like to use those 4Gb!

---

### Post by dino99 on 2010-08-09
sda8, your /home is very small (less than 10 Go) and is yet full
sda5, have plenty of free room, so reduce it first to expand sda8 (do it step by step booting with  partedmagic)

mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

### Post by maghoxfr on 2010-08-09
Ok, I'll try that. How big home partition is recomended to be?

---

### Post by dino99 on 2010-08-09
> **maghoxfr said:**
> Ok, I'll try that. How big home partition is recomended to be?

it is where your personal data are (mp3, video, ...) so give it the maximum (check the link previously given into #2)

---

