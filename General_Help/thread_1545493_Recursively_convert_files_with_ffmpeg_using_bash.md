---
title: "Recursively convert files with ffmpeg using bash?"
date: 2010-08-03
forum: General Help
---

### Post by Sohex on 2010-08-03
I have several large sets of flac files that are all organized like so: 
Artist/Album/Song.flac and I need to convert these to .alac's in order to play them on my iPod.  I have a script that will convert all the flac's in a folder to alac's and it looks like this:
```
for i in *.flac; do ffmpeg -i "$i" -acodec alac "`basename "$i" .flac`.m4a"; done;
```
The problem is that with my current file structure I have to run that in the folder of every album which would take a long time.  What I would like to do is a write a script that would just run that recursively in every folder down from my current directory, then I'd like to append a script to move all the newly created alac's to another folder in a way that retains the current structure so I could end up with something like:
/FLAC/Artist/Album/Song.flac and /ALAC/Artist/Album/Song.m4a
Any suggestions/advice/feedback would be appreciated.
Thanks for your time,
Sohex

---

### Post by David Andersson on 2010-08-04
I think it is cleaner to let ffmpeg place the .mp4 in the parallel folder struct directly.

First create the parallel folder struct without files in it. Assuming the top folder is named "Music" and the parallel is to be named "Music_too":

```
find Music -type d | sed s/Music/Music_too/ | xargs -d'\n' mkdir
```

If there is exactly two levels (album/artist), just loop with "for" like before but with more stars:

```
for i in **Music/*/*/*.flac**; do ffmpeg -i "$i" -acodec alac "`basename "**${i/Music/Music_too}**" .flac`.m4a"; done
```

(Can there be files on different folder levels? Either add more star-pattern (for i in bla/*.flac bla/*/*.flac bla/*/*/*.flac bla/*/*/*/*.flac) or elaborate with the find command.)

(Note: commands not thoroughly tested)

Edit: Now I've read your post. :) Replace Music with FLAC and Music_too with ALAC in the above.

---

### Post by Sohex on 2010-08-04
The converted m4a's show up in the directory containing Music and Music_too (or FLAC and ALAC if you will) instead of in the appropriate location, how can I fix that?
Thanks

---

### Post by David Andersson on 2010-08-04
> **Sohex said:**
> The converted m4a's show up in the directory containing Music and Music_too (or FLAC and ALAC if you will) instead of in the appropriate location, how can I fix that?

Sorry, my fault. The "basename" removes the directory part of the names.

Either replace "`basename "${i/Music/Music_too}" .flac`.m4a" with "`dirname ${i/Music/Music_too}"`/`basename "$i" .flac`.m4a" or edit $i in two steps using neither dirname nor basename, like o=${i/Music/Music_too}; o=${o%.flac%.m4a} and then use "$o" in the ffmpeg command.

```
for i in Music/*/*/*.flac; do **o=${i/Music/Music_too}; o=${o%.flac%.mp4};** ffmpeg -i "$i" -acodec alac "$o"; done
```

Put an echo before the ffmpeg the first time you run the command to see what it will do:

```
for i in Music/*/*/*.flac; do o=${i/Music/Music_too}; o=${o%.flac%.mp4}; **echo** ffmpeg -i "$i" -acodec alac "$o"; done
```

---

### Post by Sohex on 2010-08-04
Thank you so much, that works perfectly.

---

