---
title: "Halp! I warped my keyboard and can't log on!"
date: 2011-02-10
forum: General Help
---

### Post by DreymaR on 2011-02-10
I was messing around in the xkb folder trying to define a new keyboard (keycodes and geometry) for my own uses. Eventually, I got a bit desperate and moved both the .dir files and the rules/base and rules/evdev files to a backup folder in the hope that they would get rebuilt properly based on directory content and .part files at the next startup.
 
Well, ostensibly they didn't. What happened however, was a little worse than I'd expected:
 
The X server won't start, and the console layout is completely borked! Like, the Ctrl key gives the letter a etc etc. Worse, I can't find a Shift key anywhere on the keyboard which means that I cannot for the life of me log on to try and fix my problem!
 
Any helpful suggestions please? (Yes, I do feel silly now. Very.)

---

### Post by dino99 on 2011-02-10
you are ready for a new install

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by DreymaR on 2011-02-10
That bad, huh? No sneaky mounting of the linux partition while running from the live disk to restore the files to their original positions or anything like that? Ah well.  :)

---

### Post by P4man on 2011-02-10
Why not boot from a live cd, and restore the files and folders you backed up?

---

### Post by coffeecat on 2011-02-10
Do you mean /usr/share/X11/xkb? I don't know whether this will work, but try booting from the live CD, renaming the /usr/share/X11/xkb directory (in case you want it as a souvenir) and then simply copying /usr/share/X11/xkb and contents from the live session to your HD installation.

---

### Post by DreymaR on 2011-02-10
> **coffeecat said:**
> Do you mean /usr/share/X11/xkb? I don't know whether this will work, but try booting from the live CD, renaming the /usr/share/X11/xkb directory (in case you want it as a souvenir) and then simply copying /usr/share/X11/xkb and contents from the live session to your HD installation.
 
How/where do I access the HD installation while running the Live CD?

---

### Post by coffeecat on 2011-02-10
> **DreymaR said:**
> How/where do I access the HD installation while running the Live CD?

Simply mount it from the Places menu, note the mountpoint in /media and  be very careful with your syntax if you use 'cp' from the terminal. Or  open a root natuilus with 'gksu nautilus' (open two) and be careful that  you are copying from the CD filesystem to the HD filesystem.

**EDIT**: sorry, just noticed you joined the forum this month. How experienced are you with Linux? If you need more detailed instructions, just post back.

---

### Post by P4man on 2011-02-10
Simply go to places, select your drive/partition. The actual path should be 
/media/yourharddisk/usr/share....

(though /media might be /mnt not 100% sure).

if you are not sure about what partition you need, like if you have multiple installs, just run disk utility from system > administration > disk utility. You can view/mount the partitions there as well, with a nice link to open them.

---

### Post by DreymaR on 2011-02-10
Thanks guys! I'll try this out when I'm back on my mangled machine. Very helpful, kudos!

[Update: Thank you good people - the problem is now solved! I used a gksu nautilus; I had figured that much out by myself really but didn't find the Linux partition. Using Disk Utility to mount that made my day and I didn't have to figure out a command-line magic incantation for it. Again, thanks! Of course, now I'm still back to where my keyboard keycodes aren't defined as I would have them but that's a matter for another thread.]

---

