---
title: "TTA question"
date: 2011-07-21
forum: General Help
---

### Post by jamesisin on 2011-07-21
I downloaded a couple of TTA files and they are just static on playback.  Do I need a different codec or something?

Converting the files to FLAC yielded the same results.

I'm running a 10.04 64bit machine.

---

### Post by AlphaLexman on 2011-07-21
Wikipedia says VLC will play .tta files...
[http://en.wikipedia.org/wiki/TTA_%28codec%29](http://en.wikipedia.org/wiki/TTA_%28codec%29)
```
sudo apt-get install vlc
```

---

### Post by jamesisin on 2011-07-21
Yes, VLC will play these files.  That unfortunately won't get them converted to FLAC so that I can use them in the rest of my collection.

I used Sound Converter to convert them as above, but even in VLC the converted FLAC files are static (of course, right).

Perhaps another converter?  Something from the command line even?

---

### Post by jamesisin on 2011-07-21
Also, I tried using flac *tta but received an error:

```
ERROR: input file 01 Red Buddha.tta has an ID3v2 tag
ERROR: input file 02 As Expanding As.tta has an ID3v2 tag
```

---

### Post by AlphaLexman on 2011-07-21
In my experience, 'VLC' can convert ANYTHING it can play to ANYTHING it can output.

See 'Media -> Conve_r_t / Save (Ctrl+R)'

I don't have any .tta files to test however...

---

### Post by jamesisin on 2011-07-21
Aside from it being cumbersome, clunky, and counter-intuitive VLC managed to convert the audio from TTA to FLAC (after a brief learning curve ride) successfully.  However, it dropped the tags.  Any way to preserve those?

I'm still open to other solutions as well since this is less than ideal.

---

### Post by mc4man on 2011-07-21
you could try using ttaenc to convert to wav - than wav to flac

[http://en.true-audio.com/Free_Downloads](http://en.true-audio.com/Free_Downloads)

In Archive section
TTA compressor version 3.4.1 (linux x86

archive contains a binary, ttaenc, make executable, place in path (~/bin if you have one is good

ttaenc -d /path/to/.tta

Or you could try vlc > media > convert/save, setup as in screen as ex.

---

### Post by jamesisin on 2011-07-22
mc4man - Thanks.  If I convert it to wave first I'll again lose the tags.  I believe I used the exact setup you outline in your image.  This does work to convert the file, but it loses the tags.  And since it's one file at a time it's not a great long-term solution.  (This download was only two files, but let's think big and imagine a download of 100 files I want to convert.  Ugh!)  I imagine I could automate the ttaenc, but that still leaves the tagging problem.

---

### Post by mc4man on 2011-07-22
Didn't realize you had tags
Have you tried sound[COLOR="Blue"]k[/COLOR]onverter, the current one does tta using either ffmpeg or mplayer for decoding (your choice in the setup > backends, vlc likely used ffmpeg so I'd try that

I can't remember if the older Sk version would use ttaenc, though it would need to be built at this point
Edit: - if you're on lucid then you'd have the older Sk, it may show or mat not (ttaenc

Otherwise may be possible to create a batch convert script that encoded to flac and tagged, though I'm unfamiliar with tta tags

---

### Post by jamesisin on 2011-07-22
I was running SK on my 8.10 machine before I built this 64bit 10.04 machine.  I prefer to avoid the K stuff where possible, but SK is a work horse.  SC is much improved over the version on 8.10.  I'll give SK a try and see what it can do.

---

### Post by jamesisin on 2011-07-22
Looks like SK uses flac.  From the Detailed tab (Advanced Options):

```
Command: /usr/bin/flac %p -o %o %i
```

Regardless it creates a nice 0 byte file.  Not so great.

I do notice that SK says it's missing ttaenc, but I cannot find any such package to install.  Where is ttaenc?

---

### Post by jamesisin on 2011-07-25
Anyone else want to take a stab at it?

---

