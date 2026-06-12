---
title: "amaroK Cover Manager and folder.jpg"
date: 2006-03-26
forum: General Help
---

### Post by dartmusic on 2006-03-26
Does anyone know how to get amaroK to save the cover art that it finds in the appropriate album's folder as folder.jpg?

When I switched from SuSE to Kubuntu a couple of weeks ago I lost all the covers that I had downloaded with Cover Manager.  

Any ideas?

Thanks!

---

### Post by z-vet on 2006-03-27
You can keep covers that Cover Manager downloads for limited time only (legal issues with Amazon) and then amaroK delete them automatically. But covers already in album's dir? It does not manipulates them, just displays them.

---

### Post by trotski on 2006-03-27
I'm not sure about Amarok 1.3.x, but in Amarok 1.4, you can do this when you use the file organizer (right click the album in the collection browser > Manage Files > Organize... > click the "Use Cover Art" checkbox).   You get the same option when you "Move" files into your collection from the file browser.

---

### Post by z-vet on 2006-03-27
Well, i guess i misunderstood the question. Sorry.

---

### Post by dartmusic on 2006-03-28
Well, that deleted the album that I tried this on.  amaroK tried to move it (even thought I told it not to change names, etc.) and simply saved the cover art to a new folder somewhere, and deleted the original song files.  Luckily I had a copy of them elsewhere.

This is pretty standard, simple stuff.  Not sure why this isn't a simple option in amaroK.  I guess I should post something about this in their forums, eh?

Just thought someone might know something about this.

But...where is this info kept?  Such as, when I upgrade to Dapper I'll want to a fresh, clean install, but I'll lose all the artwork and such in amaroK.  Does anyone know where this info is stored?

Thanks.

---

### Post by z-vet on 2006-03-28
Ok... :) They stored in ~/.kde/share/apps/amarok/albumcovers. Copy them into albums and you all set.

---

### Post by trotski on 2006-03-28
Weird.  I have no option to tell it not to change any filenames.  It moves the file based on its tag info.

---

### Post by z-vet on 2006-03-28
Just copy them by hand to appropriate dirs and rename one by one to match albums names or something. I think there's no automation like you want in amaroK.

---

### Post by dartmusic on 2006-03-28
Sadly, I think you are correct.  It seems odd since there are programs which do this, though none that I know of for Linux.

Most of the records in my collection have artwork that I spent hours scouring the net looking for artwork (some are rare/odd/etc) and manually downloading and renaming as folder.jpg.  

I guess it's an afternoon googling for me, eh?!

---

### Post by trotski on 2006-03-28
It works for me, though.  Amarok creates a .directory file in the album directory.  Within this file, you get an entry like this:

```

[Desktop Entry]
Icon=/home/trotski/.kde/share/apps/amarok/albumcovers/cache/100@d2a67710a0719972e9c4d839f2d0ba54

```

Amarok links it to the appropriate cached image from Amazon.

Maybe this is an Amarok 1.4 feature.  I'd thought I remembered seeing it in Amarok 1.3.8.

---

### Post by z-vet on 2006-03-28
Strange. No files created by amaroK in my albums...but i don't use an "organize" feature since i don't understand how it works. However, your problem seems to be solved, right? ;)

---

### Post by dartmusic on 2006-03-28
If by raising the a white flag of surrender you mean solved, then yes, problem solved!

---

### Post by z-vet on 2006-03-28
Man... I don't see a problem, really. I gave you the path to location where downloaded album covers are stored. trotski says you can do it using an  "Organize" feature. Sorry, but i really have no clue how an "Organize" works, my experience with it is as bad as yours: i tried to use it once, but it "organizes" my albums in the way my logic can't get. I had this question about covers and how to store them by myself and found an answer: seems that there's no way to do it with amaroK without messing up your entire collection or some part of it, so the easiest solution is to navigate to ~/.kde/share/apps/amarok/albumcovers, review the files that stored there one by one and copy them to appropriate locations, then rename them as you like. I dealed with really huge amount of albums in my collection (i have about 600 mp3 CD's and some 700 albums on HDD) and i love my album covers to have the name of the album they belongs to. Sometimes i think that i'm a laziest person in the world, but i edited them by hand, one by one. Do i need to say more?

---

### Post by dartmusic on 2006-03-28
Z-vet: that's all I was saying.  Agreeing with you, I mean.

---

### Post by trotski on 2006-03-28
I think the idea is that Amarok wants to include an organizer that works like those you find in popular Windows media players.  I am rather used to the concept as I used to be a big Foobar2000 fanatic.  Of course, the config string I used in Foobar was so much cooler than what I can do in Amarok.  Anyway, I use

```

%folder/%artist/(%year) %album/%track. %title.%filetype

```

for just about everything in Amarok.

---

### Post by dartmusic on 2006-03-28
I almost feel like I'm belaboring the point, so I hope no one is bored, but:

Saving a static copy of the current artwork for an album has absolutely nothing to do with organizing your music files.  I, personally, am anal retentive (some would say to a fault) and want my music files organized the way that *I* want them.  When I add music files to my library, I put them where I think they should go and don't really appreciate software trying to change that.  Saving a jpg file shouldn't effect where your files are saved.

And, by the way, I love amaroK!  I don't feel that it's "feature complete" yet, but it does what it does well, not to mention smoothly and quickly.  Within a year, people will be switching to some form of Linux distro just to try programs like amaroK.  (Has anyone else noticed that amaroK copies files to the iPod SO much faster than iTunes?)

---

### Post by trotski on 2006-03-29
Due to the nature of Amazon's wishes in this regard, Amarok has little choice but to implement it this way.  I suppose you could just yank the cover scans out of the cache and put them in manually.  It would save you from having to scour the web.  Amarok is, of course, ignorant of your file setup.  So, an option to declare the folder as an album's folder might be useful.  Still, the files would be mere cached images.

---

### Post by linzer on 2006-03-29
In order to use covers in both amaroK and SlimServer I finally ended giving up with amaroK's built in cover manager.  Now I use Album Cover Art Download and save a copy of cover.jpg in each CD's folder.  This way both amaroK and SlimServer recognize the image.

FWIW, I installed 1.6 of Album Cover Art Download earlier this week and it appears to be offline now.  Freshmeat might have info too.

---

### Post by jms830 on 2006-07-08
you can try adding this script to amarok
[http://www.kde-apps.org/content/show.php?content=22517](http://www.kde-apps.org/content/show.php?content=22517)

---

### Post by miceagol on 2008-02-11
> **z-vet said:**
> You can keep covers that Cover Manager downloads for limited time only (legal issues with Amazon) and then amaroK delete them automatically. But covers already in album's dir? It does not manipulates them, just displays them.

How long is "limited time"? Can't find any sources on this...

---

