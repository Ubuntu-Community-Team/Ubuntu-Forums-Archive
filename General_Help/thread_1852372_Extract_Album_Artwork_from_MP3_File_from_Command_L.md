---
title: "Extract Album Artwork from MP3 File from Command Line"
date: 2011-09-30
forum: General Help
---

### Post by Kissell on 2011-09-30
Anyone know a way to do this?  I want to be able to batch script this process for my entire music collection, so I need a command line way to take the cover art out of an mp3 file and make a jpg.

---

### Post by An Sanct on 2011-09-30
Have you tried EasyTag?

This could get all the cover art into a folder (I have not tested this) and then you could make a collage in InkScape or Gimp.

---

### Post by Kissell on 2011-09-30
I have tried easytag already.  

No good.

It lets you extract the cover art from a single file at a time, but you can't do it in a large batch.  I have too much music to extract each album cover art manually.

---

### Post by An Sanct on 2011-09-30
How about any of the other listed [here]("http://www.rockbox.org/wiki/AlbumArt")?

---

### Post by aeiah on 2011-09-30
this, [http://linux.wareseeker.com/Multimedia/artwork.pl-0.1.zip/320751](http://linux.wareseeker.com/Multimedia/artwork.pl-0.1.zip/320751) which is listed on the above link can do it from the command line.

you can wrap it in a shell script that'll recursively crawl through a set of files and name the .jpg as the same name as the .mp3 (or the containing folder's name or album name)

---

### Post by Kissell on 2011-09-30
Well, it took awhile, but got the artwork.pl solution to work.  

It isn't well documented, it says you need some modules for perl but there was no clear what of how to get those.  

Then the script itself prompted for user input so there was no way to batch it without modifying the script, and I hadn't written a perl script in years, so that took awhile to figure out...  but eventually, I got it to work.  It went through my entire collection and extracted the cover art for each album.  A little caveman-ish...  it checks every mp3 file and saves the cover as "artist - album.jpg", meaning if there are 16 songs on this album it saves the same cover art file 16 times...  so slow...  but it gets the job done.

---

