---
title: "What software to use to rip VCDs into avi files?"
date: 2006-04-20
forum: General Help
---

### Post by Mishal on 2006-04-20
I have a lot of VCDs (yep, NOT DVDs) which I want to store in my HDD but I don't want to copy/paste them in their 700MB filesize. Is there any software in Linux that I can use to rip them into avi files?

Thanks in advance:D

---

### Post by az on 2006-04-20
I think thoggen can rip from VCDs.  It rips to ogg/theora, which is a free-libre video codec.

You can use acidrip, if you want to use the w32codecs and mencoder/mplayer.

There are also a number of other dvd rippers, too.

---

### Post by n00blar on 2006-04-20
This is one the topics where I wish the Linux communitry would come in and get some sort of standard, or official, application that will handle these kind of things. It's such a *project* to be able to manage (copy, backup, or rip) your own copies of DvDs. I guess soon we'll enjoy the easy and faster way that the Windows fellows have. I can just hope it won't take too long.

---

### Post by az on 2006-04-20
[QUOTE=n00blar] It's such a *project* to be able to manage (copy, backup, or rip) your own copies of DvDs. .[/QUOTE]
sudo apt-get install k9copy

Of course, you need to install the codecs and libdvdcss from the Restricted Formats wiki page....

---

### Post by unnes on 2006-04-20
If I'm not mistaken, VCDs are simply MPEG2 files, and contain the MPEG file somewhere on the CD, which you can find just by poking through the directories. Presumably, anything that can convert MPEG --> AVI should work.

---

