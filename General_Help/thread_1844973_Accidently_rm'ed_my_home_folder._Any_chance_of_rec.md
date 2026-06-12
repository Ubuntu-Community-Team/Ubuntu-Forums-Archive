---
title: "Accidently rm'ed my home folder. Any chance of recovery?"
date: 2011-09-16
forum: General Help
---

### Post by ninjaaron on 2011-09-16
Hey, I just removed my home folder with rm.  This was on purpose, as I was planning to mound another partition as my home folder.  However, I forgot that that partition was mounted inside of home when I ran the command.

I have most of my data backed up, but I'd rather not have to reinstall the system to get the config files back, on which I spent a fair amount of time.

Any way to get the stuff back?

---

### Post by staticd on 2011-09-16
You could try photorec from the cgi security site. I've found it very useful. Dont let the name fool you. works on all sorts of files, not just photos. I think it can be restricted to recover only plain text(config) files but not sure how.

I've not tried to use it but you should first try to use extundelete. wich will recover file names and inode info.

# extundelete /dev/sdax --restore-directory path/to/directory

Tell us if it worked. Need less to say DONT write to the parttion till all recovery is done.

---

### Post by SlugSlug on 2011-09-16
I'd also be interested in the recovery status

---

### Post by Rasa1111 on 2011-09-16
d'oh!

---

### Post by ninjaaron on 2011-09-16
running extundelete now.  It's definitely doing *something.*

Somethings are recovering, some things are restoring.  others not... oh it finished... let's see here...

*****

ran out of space, as tried to load everything in to my system directory, and that is only 10 GB.

Doing it again with my external drive, which has something like 80 GB free (which is about 20 less than the used space on the partition I'm trying to recover,  It's mostly the same data on both... I just hope it can get the stuff that isn't the same...)


[edit] looks like it will have space.  Most of the things it's failing on are high-def movies and music and stuff, which isn't what I'm interested in.

---

### Post by ninjaaron on 2011-09-16
Alright, it recovered all of the config files about which I was specifically worried, though it missed some files I would like to have seen (but I believe they are all backed up on my external or UbuntuOne. I may have lost a few recently-downloaded songs).

Let's hope it got enough of the config files that I wasn't thinking about to have a working system without too many surprises.

moving the data back to it's proper place now...

---

### Post by ninjaaron on 2011-09-16
So, I moved my flies back "home," and my environment is up and running again, after a little bit of hide-and-seek with permissions.

A lot of the "big data" is gone, and I lost two firefox addons, but I have all but the most recent elsewhere.  extundelete got the stuff that I was looking for. thanks staticd!

Solved.

Yay!

---

