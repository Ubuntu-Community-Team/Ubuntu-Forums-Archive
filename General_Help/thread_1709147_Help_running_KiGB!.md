---
title: "Help running KiGB!"
date: 2011-03-17
forum: General Help
---

### Post by pjdougherty on 2011-03-17
Sorry to bother you all about something everyone seems to have figured out a few years back, but hopefully someone can help me. I've been using Ubuntu 10.10 for a while but am still learning terminal commands. I'm trying to use KiGB v2.02, the newest version, but I can't get it to open. I did exactly what the readme file said: 

"To set up HawkNL library, copy the file libNL.so.1.6.4 to /usr/local/lib.
    Then, change directory to /usr/local/lib. Add a soft link: ln -s
    libNL.so.1.6.4 NL.so.1.6. You have to be root to do this."

I can't say conclusively if I'm running a 32- or 64-bit distribution, only that I have i686 showing up in terminal. Hopefully that means more to you than it does to me.

Any help you can provide would be very much appreciated. Again, I'm really sorry to bother you with this, but I just can't figure out what to do.

---

### Post by pjdougherty on 2011-03-18
Okay so I figured that problem out on my own; I tried putting the files in /usr/lib instead and that allows KiGB to open. Now that it's open, I have another problem: when I open a rom, the emulator freezes. Nothing loads, no button shortcuts work, the file menu disappears, and the close application button won't even work. If anybody has any help on this, it's like gold to me. Thanks!

---

### Post by TrekBaum on 2011-03-24
Yours is definitely 32-bit. "uname -m" would say amd64 otherwise.
I am at the same stage of installing KiGB and am having the same problem on 32-bit. 
One thing that I found out is that Ubuntu 10.10 does not have libstdc++5 from a fresh install. I had to install the package just to open kigb.

When I try to directly load the rom ie "./kigb /home/..../PokemonBlue.gb" it returns "segmentation fault." Perhaps someone wiser than I could interpret this.

I would appreciate help with this thread, also. Thanks.

---

### Post by Asig on 2011-10-21
Hello, I know this is an old thread but I have the same problem as pjdougherty and couldn't find a solution.

I'm on ubuntu 11.10 64-bit, so I had to install the extra packages (libstdc++5 and ia32-libs) to be able to run kigb. I finally got it to run, but when I try to load a rom it completely freezes, the menu disappears, and I can't close the window.

Any help would be very much appreciated, thanks.

---

### Post by SketchMan3 on 2012-06-14
I have the same problem. I can't get KiGB to do anything at all, whether I run in terminal or just try to double-click the binary file.

---

### Post by benben591 on 2013-04-25
Hey I have a problem. I played pokemon crystal on my KiGB for a while, but I want to play yellow. I try opening it, but it opens pokemon crystal, I deleted crystal, yellow, and KiGB, re-downloaded, and nothing. Please help me!

---

