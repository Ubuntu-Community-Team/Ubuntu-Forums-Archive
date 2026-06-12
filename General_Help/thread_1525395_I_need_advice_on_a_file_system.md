---
title: "I need advice on a file system"
date: 2010-07-06
forum: General Help
---

### Post by hopeless8009 on 2010-07-06
I"m about to reformat my external USB hard drive. I plan to mount it on my 10.4 Ubuntu file server. I am kind of new to Ubuntu. I've been running it for about 4 months now. I don't know what file system would be best for the hard drive, because i don't know any thing about Linux file systems. There are windows computers in the home so it would be nice to have a file system they could see, and its on a server so it has to be able to be accessed fast. if the Linux file system is better then I don't care if the windows computers see it or not.

---

### Post by Seanlol on 2010-07-06
Ext4 is certainly better than NTFS, imo. No need to worry about fragmentation and it's faster. But Windows computers can't access Ext4 innately, though I do believe there is a program or add-on or something like that which will let them see Ext4.

---

### Post by stlsaint on 2010-07-06
IF you dont care about windows compatibility than ext4 will do fine. But i would suggest ntfs "just in case" you feel the need to access it from windows or if anyone else in your home wants to access it. Also yes windows can access ext4 drives, some research will go more in depth on this setup.

---

### Post by hopeless8009 on 2010-07-06
its a 500GB drive so i guess I'll half and half. is ext4 stable? is ext3 more stable then ext4? what is the diffrence between the two?

---

### Post by WorMzy on 2010-07-06
Both ext3 and ext4 are stable, but I'd recommend you use ext3 for an external hdd. There's more support for ext3 on the Windows side. If you're looking for speed, maybe try formatting as ReiserFS or XFS. I haven't used them myself, but they're considered "fast" filesystems.

---

### Post by hopeless8009 on 2010-07-06
what do i use to format them with thows file systems i might but a small test system on.

---

### Post by hopeless8009 on 2010-07-06
> **WorMzy said:**
> Both ext3 and ext4 are stable, but I'd recommend you use ext3 for an external hdd. There's more support for ext3 on the Windows side. If you're looking for speed, maybe try formatting as ReiserFS or XFS. I haven't used them myself, but they're considered "fast" filesystems.

ReiserFS was the default file system in [Novell]("http://en.wikipedia.org/wiki/Novell")'s  SUSE Linux Enterprise until Novell decided to move to [ext3]("http://en.wikipedia.org/wiki/Ext3") on  October 12, 2006 for future releases.[]("http://en.wikipedia.org/wiki/ReiserFS#cite_note-shankland1-0")

---

### Post by hopeless8009 on 2010-07-06
I decided to format it ext 4. when it has you click to take premisions of the hard drive do it. im formating it on my laptop not the server

---

### Post by WorMzy on 2010-07-06
> **hopeless8009 said:**
> ReiserFS was the default file system in [Novell]("http://en.wikipedia.org/wiki/Novell")'s  SUSE Linux Enterprise until Novell decided to move to [ext3]("http://en.wikipedia.org/wiki/Ext3") on  October 12, 2006 for future releases.[]("http://en.wikipedia.org/wiki/ReiserFS#cite_note-shankland1-0")


Is that important to you? I imagine they made the switch due to ext3 using journaling, making it somewhat safer than Reiser.

---

### Post by hopeless8009 on 2010-07-06
when i was in school i trained in Novell so i know if they switched to it it must be better. the speed is nice but since its on a server its important to have fault protection. you know what i mean.

---

### Post by davidogg on 2010-08-12
> **WorMzy said:**
> Is that important to you? I imagine they made the switch due to ext3 using journaling, making it somewhat safer than Reiser.

Reiserfs has journalling too.

---

### Post by linux18 on 2010-08-12
> **davidogg said:**
> Reiserfs has journalling too.
reiser fs journaling isn't nearly as good *** ext3/4 journaling, I've has data loss with reiser in power outage situations

---

