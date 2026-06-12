---
title: "re-organizing pictures"
date: 2010-12-11
forum: General Help
---

### Post by burnclouds on 2010-12-11
I have a pictures directory with the following structure:

~/Pictures/A/a/001.jpg
~/Pictures/A/a/001.JPG
~/Pictures/A/b/001.jpg
~/Pictures/A/c/001.jpg
~/Pictures/B/001.jpg
~/Pictures/C and D/a/001.jpg


I'd like to have them all copied and renamed so I have something like:

~/pics/00001.jpg
~/pics/00002.jpg
~/pics/00003.jpg
~/pics/00004.jpg
...

My bash/python kungfu is simply not strong enough for this.

I've tried this:
find ~/Pictures -iname *.jpg exec cp -vi --target ~/pics/ "{}" \;
but get multiple overwrite warnings (obviously) due do the multiple 001.jpg files.

---

