---
title: "I wish to do something strange....and need help"
date: 2006-06-08
forum: General Help
---

### Post by Invisible on 2006-06-08
These probably are not the best forums for this, but anyway here goes.

I run Ubuntu as my primary OS on one of my two computers, it runs on my primary master hard drive.

On my primary slave HDD I also have Yoper linux OS (graphically very sexy, but that is about it), and on my final HDD I have nothing.

Now on my Secoundry master (third hdd), the one that is empty, I wish to install windows xp home.

Why? simple, I find that linux cannot run some applications that are designed for windows only (and WINE cannot run them either). I admit that most of these applications are games (eve-online and the like).

So what is my problem, simple, when I come to install windows xp home on my third HDD, it does not. I can format the drive to RAW, but cannot create a FAT32, or NFTS partition, and so I cannot install windows. The create partition function on the windows disk refuses to do it.

So how can I install windows on this disk without having to install over Ubuntu or Yoper?

---

### Post by johnc4510 on 2006-06-08
It is my understanding that Windows must be in the first position of any multi boot system. This is not a Linux thing, it is a Microsoft thing.

---

### Post by ticool on 2006-06-08
You have to connect your secondary master to Primary Master and then Install Windows.... After that you rebuild your drive order as it was...
Then you just modify GRUB to fit your Partions and to boot windows!
This should definitly Work..

---

### Post by scaine on 2006-06-08
Yep - I can confirm John's take on this.  Dunno about ticool's solution.  I had a set up very similar to Invisible, and when I tried to install Windows, it refuses to acknowledge the empty space on my big, third drive.

I had to create a 1Gb partition on hda1 for Windows to use to install it's boot loader.  It could probably be tiny, but I used 1Gb.

Then you can tell windows to install into the big empty space on drive three, but you NEED that tiny NTFS partition on your primary hard disk before Windows will continue.  Don't make the mistake of thinking that you've fooled it either - even when you say, "use the third disk", it'll still warning you that it's about to format the first one for it's boot loader.  Then it'll quite happily install all it's files onto the third disk.

Crappy Microsoft.  I had to re-install Ubuntu after making the necessary partition changes.  Not that it took long, but still.

---

