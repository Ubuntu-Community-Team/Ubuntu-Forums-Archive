---
title: "Randomly Corrupted xorg.conf"
date: 2006-02-01
forum: General Help
---

### Post by nrwilk on 2006-02-01
Today I started up the box and all I got when it finished booting was a text prompt.  I saw an error about something wrong with xorg.conf, and when I opened it up in vi, there were all sorts of weird random characters all throughout the file.  I deleted them all, and got several other errors with xorg.conf.  I fixed the issues (more characters that I had missed).  Now, after a reboot everything works as normal.

My question is, what corrupted xorg.conf?  Why did this happen?  should files just get randomly corrupted?

I haven't done anything with xorg.conf for a while, and I haven't installed any software that would mess with it.

---

### Post by Leif on 2006-02-01
what filesystem are you using ? if it's reiser, it has been known to cause problems, albeit rarely. or it could be that your harddisk itself is nearing its end. I'd suggest a full backup, and a filesystem check

---

### Post by nrwilk on 2006-02-01
No, I'm using ext3.

I have 33GB left in my /home partition, and 7GB left in my / partition

---

### Post by Leif on 2006-02-02
I meant a fsck check. do "sudo shutdown -rF now" to reboot and run fsck, and see if it gives any errors.

---

### Post by Lord Illidan on 2006-02-02
[quote=Leif]what filesystem are you using ? if it's reiser, it has been known to cause problems, albeit rarely. or it could be that your harddisk itself is nearing its end. I'd suggest a full backup, and a filesystem check[/quote]

Where is it said that it can cause problems? I'd like to know, because I am holding quite some valuable data here... (losta pr0n, you know...;););) )

---

### Post by Leif on 2006-02-02
[QUOTE=Lord Illidan]Where is it said that it can cause problems? I'd like to know, because I am holding quite some valuable data here... (losta pr0n, you know...;););) )[/QUOTE]

well, nowhere official really, but read quite a few anecdotes (places like slashdot, fedora forums, and these forums). sometimes bad rumours get out of hand, but they were enough to make me stick to ext3.

---

### Post by sisooktom on 2006-02-03
Yeah, I've had this happen too, but I'm not sure what causes it.  I think it's one of the configuration tools but I haven't had it happen enough to pin down which one.

---

### Post by nrwilk on 2006-02-03
[QUOTE=sisooktom]Yeah, I've had this happen too, but I'm not sure what causes it.  I think it's one of the configuration tools but I haven't had it happen enough to pin down which one.[/QUOTE]

I haven't used any xorg.conf config tools, though.  I don't even think I have any installed.  I've always edited xorg.conf by hand.  Are there config tools that are installed by default that could mess with it even if I haven't ever started them?

---

### Post by nrwilk on 2006-02-06
OK, it happened again.  That's twice in four days.

I just remembered that I recently used the kubuntu install disk to resize my home partition.  But, that can't be the cause of this problem because /home is on a seperate partition from my / partition, where /etc/X11/xorg.conf is located.  And none of the extra space that I allocated to my /home partition came from the / partition.  So, the / partition shouldn't have been affected in this resizing at all.

Any other Ideas about what this could be?

This is really weird!

Attached is a copy of the corrupted xorg.conf.  If you want to really see the corrupted parts, open it with vi.  Graphical editors don't see all the characters that make up the corrupted parts.

---

