---
title: "Music folder help."
date: 2010-02-19
forum: General Help
---

### Post by venividibitchy on 2010-02-19
I used MusicBrainz Picard to tag FLAC and Mp3 files, fixed any necessary genre tags in Rhythmbox, and used EasyTag to rename the actual files.

But now I'm interested in using those genre tags as folder names...is there any program that will sort my music into folders based on their genre tags?

Thanks-

---

### Post by n0dix on 2010-02-19
If is not already program for this a would like to create this feature. I try to do using python.

---

### Post by joeknoodle on 2010-02-19
> **n0dix said:**
> If is not already program for this a would like to create this feature. I try to do using python.
I'd recommend such a program would be able to sort genres as either by the song itself, or by the artist - preferring both methods available.

I call Johnny Cash "Rock" (for my own reasons), but many of his songs end up being under the "Country" genre.

So, I put all of Johnny's folder inside my "Rock" folder, even if some individual songs within are under the "Country" genre in Rhythmbox.

---

### Post by mechro on 2010-02-19
EasyTAG will do it...

In EasyTAG select all your music files you want to sort, then do...

**Scanner > Rename File(s) and Directory...**

In the **Tag and File Name scan** box that opens create a Rename File and Directory...

Example **/home/username/Music/%g/%a - %t**  will create Folders by genre containing files listed by artist and title.

Then do **File > Save File(s)**

---

### Post by claracc on 2010-02-20
Perhaps you can give lltag command a try.

Here, there is a link explaining how to use [http://home.gna.org/lltag/](http://home.gna.org/lltag/)

---

### Post by venividibitchy on 2010-02-20
> **mechro said:**
> EasyTAG will do it...

In EasyTAG select all your music files you want to sort, then do...

**Scanner > Rename File(s) and Directory...**

In the **Tag and File Name scan** box that opens create a Rename File and Directory...

Example **/home/username/Music/%g/%a - %t**  will create Folders by genre containing files listed by artist and title.

Then do **File > Save File(s)**

I tried this, and it worked for scanning the files, but when I went to save them, it kept saying it couldn't create a folder titled "Lossy" which is one of my existing folders that I chose to use...

I did:[B]
home/username/Music/Lossy/%g/%a - %t[/B]

What happened?

ETA: I tried again, using /%g/%a - %t, which worked better, until I tried to save, and it keeps telling me it can't rename files and can't create directories, because of permissions...

ETA2: Hurrrr, did gksudo easytag, and it is working okay now.

---

