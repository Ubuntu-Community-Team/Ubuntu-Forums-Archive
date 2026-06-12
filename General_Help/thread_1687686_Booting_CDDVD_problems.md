---
title: "Booting CD/DVD problems"
date: 2011-02-14
forum: General Help
---

### Post by Bankbok on 2011-02-14
Here's the thing. I am trying to uninstall ubuntu 9.10 and install windows 7 instead on one of my computers. The problem is that the cd/dvd does not boot when starting the computer. I've tried the disc on a computer running with windows and it had no problems booting it. I've also tried other dvd's on my ubuntu computer and there seems to be no problem with the actual cd/dvd drive. 

Any ideas on how to solve this?

Thank you!

---

### Post by coldraven on 2011-02-14
This is just a guess.
If your 9.10 installation is occupying the whole drive then maybe your Windows boot disc cannot detect it, as it's all formatted to EXT3.
If you have removed all your important data from the drive then try formatting the whole thing with NTFS before trying to install Windows.
Then Windows will see a shiny new drive for it to install itself to.
To format, boot up with a Live CD and use gparted or download PartedMagic from here and use that. [http://partedmagic.com/doku.php?id=start](http://partedmagic.com/doku.php?id=start)
It will always come in handy.

---

