---
title: "Hiding folders inside of shared folders"
date: 2010-03-27
forum: General Help
---

### Post by hotstovejer on 2010-03-27
Hi all,

I am setting up a lubuntu nas with all of my music, movies, etc on it. I want to give my kids access to my mp3 directory, so I can move all of the kid appropiate music into the root of my mp3 dir, in the same order I have all of my music sorted. 

Under the Music folder, I have them sorted, in folders, by letter. So A, B, C, D, etc... Now, in those folders are the respective artists. So where there may be something approipate in the P folder (say, Paramore), there is something inapproipate (say, Pantera)

Now, when the kids go to the P folder, I don't want them to even see the Pantera folder. I just want them to see the Paramore folder. I tried a test using chmod 711 and chmod 700 on a directory with a test user, and the user can't access the directory, but can still see it. 

Any way to not even have it show up in Nautilus if I give it a certain permission? Should I be using chown then something else?

Thanks!

Jeremy

---

### Post by patchwork on 2010-03-27
Normally I would suggest 'hiding' the inappropriate folders by renaming them with a period (.) in front of the name (.Pantera, for instance).  However, after a bit of googling, it seems that the alpha versions of the new pcmanfm (the file manager for lubuntu) were buggy, and if you forget to turn off the 'Show Hidden' feature, the file manager will not open again.  My understanding is that the beta version is the version included with lubuntu, but I cannot seem to find any indication that the hidden file crash has been fixed (or any indication that it hasn't been fixed).  

Here's a [link]("http://forums.linuxmint.com/viewtopic.php?f=175&p=256461") to one of the sources I've seen.  I know it's from the Mint site, but a little googling will show more sources that report the same problem.

If you're not comfortable trying to fix a broken file manager, I would wait until you can be absolutely sure that this problem has been fixed.

Hope this helps.

---

### Post by hotstovejer on 2010-03-27
Well, I tested this out on a regular ubuntu box, and the nas is lubuntu. On the regular ubuntu box, the issue still exists. I know I could hide the folders with a ., but permissions should still allow if I say not to list the folders, to not list them, as opposed to showing them and saying they're not available.

Thanks for the idea! Anyone else have any idea?

Thanks!

Jeremy

---

### Post by hotstovejer on 2010-03-29
Whee! Solved!

Samba has a parameter that is called "hide unreadable = yes". That allows you to hide stuff based on permissions.

Thanks for all your help!

Jeremy

---

