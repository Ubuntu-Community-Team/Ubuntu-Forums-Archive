---
title: "How can I change fps of subtitles?"
date: 2010-01-28
forum: General Help
---

### Post by Linuxman. on 2010-01-28
I want to change fps of subtitles.I have one program in Windows(subtitleworkshop) but it's not working exactly.
Now I'm interesting is it possible change fps of subtitles in Linux? Has any program in Ubuntu?

---

### Post by chewearn on 2010-01-29
I use [Subtitle Editor]("http://home.gna.org/subtitleeditor/")

Installation from the repository [click here]("apt://subtitleeditor") or:
```
sudo apt-get install subtitleeditor
```

---

### Post by Linuxman. on 2010-01-29
Can I integrate subtitle(s) to film with this program?

---

### Post by chewearn on 2010-01-29
> **Linuxman. said:**
> Can I integrate subtitle(s) to film with this program?

Not that I know of.  For that, you need a stream muxer program, like mkvmerge (GUI) or Avidemux.

---

### Post by Linuxman. on 2010-01-29
Ok.Thank you.I will try this programs.

---

### Post by Linuxman. on 2010-02-01
> **chewearn said:**
> Not that I know of.  For that, you need a stream muxer program, like mkvmerge (GUI) or Avidemux.

I have installed Avidemux.Can you help me ? How can I integrate?

---

### Post by chewearn on 2010-02-02
> **Linuxman. said:**
> I have installed Avidemux.Can you help me ? How can I integrate?

1. Open the video.
2. On the left side of the window, select the transcode option for video and audio.
3. Select container format.

4. Menu > Video > Filters
Select "Subtitle" (left side of dialogbox).

The rest should be self explanatory.

---

### Post by ImperialXT on 2010-02-02
editing subtitles should be done in aegisub

only decent software for it.

---

### Post by AlexAv on 2011-02-02
Hey here I am one year after the last reply, just to give another "thanks" for the advices...

SubtitleEditor works like a charm... ;)

---

