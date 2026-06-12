---
title: "how to mount, hopefully play, a dvd"
date: 2010-07-21
forum: General Help
---

### Post by roberto.tomas on 2010-07-21
I have a dvd, I'd like to watch it if possible.

my system is a powerpc, with ubuntu lucid.

if I put my dvd in, and do "sudo mount /media/dvdrw" -- it mounts, but the icon disappears right away. the /var/log/messages has no message about the loss of mount point, it's just silently disappearling.

if I use vlc, (it prefers /dev/hda to /dev/dvdrw), it does not resize. it does not play. if I press play it will appear to do something, like I would expect next the window to resize and the video to appear. I see the title of the dvd flash in the status panel, but then it just stops again.

---

### Post by dineshs on 2010-07-21
Have you tried smplayer?

---

### Post by PRC09 on 2010-07-21
Try the following link....



[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by rubylaser on 2010-07-21
Just follow these directions. They're pretty straightforward.
[https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

---

### Post by roberto.tomas on 2010-07-21
thank you guys 

> **rubylaser said:**
> Just follow these directions. They're pretty straightforward.
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

thanks ruby, I think it might be the specific dvd I'm looking at now that is the issue because since doing the install-css.sh thing i can mount the disk, and start to play it but it will still fail to play past the first VOB (the rating screen).. if I manually double click the vobs they are black, if I seek in them, or if I let it play they are mosaics of mostly green tiles :P

the dvd is the painted veil .. other than the mark saying that it is copy protected, I dont see any special markings as to how they did it.

when I played Babel, a second DVD, it worked just fine. :) so thank you!

---

### Post by rubylaser on 2010-07-21
No problem, glad that fixed it for you.

---

