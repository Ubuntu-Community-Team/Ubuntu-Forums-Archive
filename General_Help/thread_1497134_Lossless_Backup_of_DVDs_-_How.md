---
title: "Lossless Backup of DVDs - How?"
date: 2010-05-30
forum: General Help
---

### Post by KingBongo on 2010-05-30
Hi. I would like to create *lossless* backups of my DVDs, or more exactly the main movie including one or more audio tracks and a subtitle of my choice. I would like to have the subtitle burned into the movie so that I only have one file (container). No, I don't want a complete DVD folder (TS_Video and other stuff) nor do I want to create an iso file of the DVD. Is it possible? 

The way I see it there should be two options:

1. Extract the wanted audio track/tracks, one subtitle and the main movie. Keep the audio track/tracks and the movie track in their original formats, and put it all together in one file/container (subtitle burnt in). In theory it should work! I know the video tracks are mostly MPEG2 and the audio tracks mostly AC-3 or DTS.

2. Do almost exactly as above, but before putting it all together compress the video and audio tracks even further to some lossless formats. In theory this should work too! In some other forum a guy told me that since MPEG2 and AC-3/DTS are already compressed formats it probably isn't possible to compress audio and video much further without losses, which is probably true.

Is it possible to do what I want to do? How? Can Handbrake be of any help? 

PS. If this process is not easy to do it would be nice if some of the skilled guys would create an application that does exactly this. I believe more than me would find it extremely useful.

---

### Post by JohnAStebbins on 2010-05-30
> **KingBongo said:**
> Hi. I would like to create *lossless* backups of my DVDs, or more exactly the main movie including one or more audio tracks and a subtitle of my choice. I would like to have the subtitle burned into the movie so that I only have one file (container). No, I don't want a complete DVD folder (TS_Video and other stuff) nor do I want to create an iso file of the DVD. Is it possible? 

The way I see it there should be two options:

1. Extract the wanted audio track/tracks, one subtitle and the main movie. Keep the audio track/tracks and the movie track in their original formats, and put it all together in one file/container (subtitle burnt in). In theory it should work! I know the video tracks are mostly MPEG2 and the audio tracks mostly AC-3 or DTS.

2. Do almost exactly as above, but before putting it all together compress the video and audio tracks even further to some lossless formats. In theory this should work too! In some other forum a guy told me that since MPEG2 and AC-3/DTS are already compressed formats it probably isn't possible to compress audio and video much further without losses, which is probably true.

Is it possible to do what I want to do? How? Can Handbrake be of any help? 

PS. If this process is not easy to do it would be nice if some of the skilled guys would create an application that does exactly this. I believe more than me would find it extremely useful.

x264, and thus handbrake has a lossless mode (set quality slider to max). But the resulting file is likely to be larger than the original. You're mpeg-2 is first uncompressed, so x264 sees only full uncompressed frames, then this is recompressed losslessy.  So the comparison is:
1. Uncompressed --> mpeg-2 lossy compression --> yields file size X
2. Uncompressed --> h.264 lossless compression --> yields file size Y

mpeg-2 lossy will pretty much always beat h.264 lossless in file size.

So option 1 is most likely what you want.  I'm not sure, but OgmRip may be helpful.

---

### Post by KingBongo on 2010-05-31
JohnAStebbins:
Thank you! I will take a further look into it. 

Now, if some clever guys would create a simple application that is concentrated on *lossless* extraction and transformation of multiple formats (video, sound), nothing more. What about something like "Handbrake Lossless"? I am not skilled enough to do it, but I believe that since the framework is strict (lossless) it wouldn't be too hard. Sorry, shouldn't open my mouth before I can do it myself ;)

---

### Post by StuartN on 2010-05-31
> **KingBongo said:**
> the main movie including one or more audio tracks and a subtitle of my choice. I would like to have the subtitle burned into the movie so that I only have one file (container).

**vobcopy -l** will automatically determine your DVD device, locate the largest / most chapters titleset and write it into a single VOB file in the current directory.

**mplayer -dvd-device /dev/dvd1 dvd://1 -ovc copy -oac copy title1.vob** will do much the same (here copying titleset 1), and you could find the correct titleset using **lsdvd /dev/dvd1**

---

### Post by KingBongo on 2010-05-31
StuartN:
Thank you! Great! I hope this is without losses too. Do these alternatives copy (all) the audio tracks and burn the subtitles into the movie as well?

---

### Post by StuartN on 2010-05-31
Copying the VOB files creates a file of identical quality to the original, with all the contents of the original - multiple languages, subtitles etc. I suppose even the chapters are in there too. Avidemux is quite useful for basic cutting and splicing, or language selection.

Personally, I much prefer my commercial DVDs without the menus, adverts and other lint, so this method works well for me. A 1 TB mediaplayer costs about 150 euro here and holds about 250 movies (at 4 GB per movie), so it is an economical backup as well.

---

### Post by KingBongo on 2010-06-01
StuartN:
Great! I think I have what I need so I will mark this thread as "solved". Thanks!

---

