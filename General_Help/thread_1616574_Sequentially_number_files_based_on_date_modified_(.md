---
title: "Sequentially number files based on date modified (rename cli)"
date: 2010-11-08
forum: General Help
---

### Post by phr0ze on 2010-11-08
Sequentially number files based on date modified (rename cli)

I need help, I'm almost done a larger script which takes all the pictures in a folder, converts it to video, and emails it to me. Everything worked fine until I realized the picture filenames weren't always starting at 1, then ffmpeg chokes.

I have a bunch of files in a folder which I need to rename to:

00001.jpg
00002.jpg
00003.jpg
etc.

I don't want to install any additional packages and I'd like this to run in a single command if possible.

If not possible, then a bash script would work too.

Thanks for any help.

John

---

### Post by aromo on 2010-11-08
partial solution:
find /path -name *.jpg -printf "%p,%t"

This command will output a CSV with the jpg files and the time they were modified.  Pass this output to sort and then to awk to do the actual renaming.  e.g. find ... | sort ... | awk ...

---

### Post by FakeOutdoorsman on 2010-11-08
The FFmpeg FAQ has an example bash command for renaming into a sequence:

[How do I encode single pictures into movies?](http://www.ffmpeg.org/faq.html#SEC14)

I haven't tried it myself.

---

### Post by phr0ze on 2010-11-08
> **FakeOutdoorsman said:**
> The FFmpeg FAQ has an example bash command for renaming into a sequence:

[How do I encode single pictures into movies?](http://www.ffmpeg.org/faq.html#SEC14)

I haven't tried it myself.

Perfect, thanks. I guess I should have RTFM.

---

