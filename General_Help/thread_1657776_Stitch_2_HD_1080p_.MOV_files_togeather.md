---
title: "Stitch 2 HD 1080p *.MOV files togeather?"
date: 2011-01-01
forum: General Help
---

### Post by gypsumwolf on 2011-01-01
Ubuntu 10.10

What is the best way to stitch 2 separate video files together.
They are HD 1080p *.MOV.

I found this tutorial but its for *.AVI.
[http://www.learnosity.com/techblog/index.cfm/2008/1/12/Joining-video-files-in-Ubuntu]("http://www.learnosity.com/techblog/index.cfm/2008/1/12/Joining-video-files-in-Ubuntu")

---

### Post by solar george on 2011-01-01
Yeah that won't work for anything except AVIs, you can however you can use MKV File Creator (you need apt://mkvtoolnix-gui installed) to combine them inside a .mkv file without the need to re-encode them.

---

### Post by gypsumwolf on 2011-01-01
Cool.

So.. Just add the 2 *.MOV files to the input and then start muxing? or do I need to convert each file to *.mkv files than link them with segment UIDs?

When I simply add the two *.MOV files then after it runs the single file I try and play in VLC and it plays both in separate windows from the single *.mkv file instead of playing like one long movie.

---

### Post by solar george on 2011-01-01
You need to use the add button for the first one then append for the second otherwise it will play them simulatneously.

---

### Post by perspectoff on 2011-01-01
Will it work to cat them?

I know that works for me for .mpg (MPEG-2) files.

cat video1.mpg video2.mpg > video3.mpg

OIC, that's what is in the blog reference you posted. (Heck the actual command is shorter than the blog reference).

You could always convert them to .avi or .mpg, cat them, and convert them back...

---

### Post by solar george on 2011-01-01
> Will it work to cat them?
No I do not think so, more complex file formats (to be more precise *container formats*) cannot simply be catted together because it would mean that the index (needed to seek) and file headers (from the first file) do not match the combined file and so appear to the player to be corrupted, even avis which are extremely simple need re-indexing if you cat them together.

---

### Post by gypsumwolf on 2011-01-01
> **solar george said:**
> You need to use the add button for the first one then append for the second otherwise it will play them simulatneously.

Thanks works well, except I put the first one last and last one first. oops. lol.

---

### Post by davidvandoren on 2011-01-02
Install cinelerra
It supports mov

[http://cinelerra.org/getting_cinelerra.php](http://cinelerra.org/getting_cinelerra.php)

Go to settings format and choose 1080 from the drop down menu

When rendering choose Quicktime for linux

---

