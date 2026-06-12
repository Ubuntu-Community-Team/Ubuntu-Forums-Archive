---
title: "Recovery from a woops!"
date: 2009-07-09
forum: General Help
---

### Post by Swizzle on 2009-07-09
I made the mistake of trying to get rid of the KDE desktop option I had recently downloaded to my Gnome Ubuntu load (9.04) by using Synaptic Pkg Manager to uninstall everything that started with "K".  Unfortunately, I also deleted the KDM apps that allowed the GRUB to boot the desktop.  I've reinstalled Jaunty alongside the original partition and can see into my original Ubuntu partition and have recovered all of my critical files.  Is there any way I can recover my e-mail and Firefox bookmarks before I dump tho old partition?  Hoping someone can help......Cheers, Swiz.

---

### Post by sdlynx on 2009-07-09
Can you read the home directory from you old partition? If so, just go to that partition's /home/user/ and press Ctrl + H (show hidden files).  You'll want to go into .mozilla, then firefox, then something like kqul04x1.default, and copy bookmarks.xml into the same directory for your current partition.  Do some snooping around the . folders in your home directory and I'm pretty sure you'll find your email too.

---

### Post by DeMus on 2009-07-09
> **sdlynx said:**
> Can you read the home directory from you old partition? If so, just go to that partition's /home/user/ and press Ctrl + H (show hidden files).  You'll want to go into .mozilla, then firefox, then something like kqul04x1.default, and copy bookmarks.xml into the same directory for your current partition.  Do some snooping around the . folders in your home directory and I'm pretty sure you'll find your email too.

Firefox bookmarks are not stored in the .xml file but in a sqlite file, probably places.sqlite but this I do not know for sure.
So better copy the whole firefox folder to make sure you have all your need.

---

### Post by sdlynx on 2009-07-09
> **DeMus said:**
> Firefox bookmarks are not stored in the .xml file but in a sqlite file, probably places.sqlite but this I do not know for sure.
So better copy the whole firefox folder to make sure you have all your need.

oh really? I figured it would make sense since it was there lol but ok

---

### Post by DeMus on 2009-07-09
> **sdlynx said:**
> oh really? I figured it would make sense since it was there lol but ok

Have a look in your bookmarks file and see if all your bookmarks are there. Also the ones you added lately.
You can however export them to an html file, but that would mean having Firefox running which for the OP is impossible at the moment.

---

### Post by sdlynx on 2009-07-09
> **DeMus said:**
> Have a look in your bookmarks file and see if all your bookmarks are there. Also the ones you added lately.
You can however export them to an html file, but that would mean having Firefox running which for the OP is impossible at the moment.

good point yeah you're right

---

