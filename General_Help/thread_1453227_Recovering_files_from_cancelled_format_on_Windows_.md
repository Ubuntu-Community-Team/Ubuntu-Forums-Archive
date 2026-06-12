---
title: "Recovering files from cancelled format on Windows drive with LiveUSB"
date: 2010-04-13
forum: General Help
---

### Post by Fryphax on 2010-04-13
Hello everyone, I've been scouring the internet and these forums for answers and have yet to figure anything out.

Here's the situation: My boss's computer (HP running Vista) decided it didn't want to boot anymore. (Error: Cannot find Bootlog.xxx) My boss used a recovery disk to attemp a 'repair' but unintentionally began a format cancelling it at 1-3%. 

I created a LiveUSB that I can boot off of, and Ubuntu recognizes 52gb of Data on the drive. However when I go to view the drive nothing is there. I am assuming that the 'page file' was deleted although the rest of the information wasn't. 

My question is: Is there anyway to access this data although the information telling the computer what is there and where it is has gone AWOL? If anyone can help me out it would be greatly appreciated. 

I'm trying to get the payroll information off of the computer so she can finish her taxes, I will be working on this all night. If anyone wants to provide real time help my AIM screen name is 'Fryphax'. 

Thanks in advance!

---

### Post by crom.osec on 2010-04-13
try testdisk:

```

apt-get install testdisk

```

I was able to recover my lost data using that great tool

---

### Post by Fryphax on 2010-04-13
> **crom.osec said:**
> try testdisk:

```

apt-get install testdisk

```I was able to recover my lost data using that great tool

This seems to be what I need to do but I am having a hell of a time getting it to run!

---

### Post by Fryphax on 2010-04-13
Try and try as I may, following many tutorials I can not install testdisk. Grr! This is what I get for not using linux for nearly a decade.

---

### Post by ronnielsen1 on 2010-04-13
Puppy Linux has a puplet that has testdisk installed. It works great.

[http://sourceforge.jp/projects/toplinux/downloads/43860/TOP-unlimited-4.2.1.iso/](http://sourceforge.jp/projects/toplinux/downloads/43860/TOP-unlimited-4.2.1.iso/)

---

