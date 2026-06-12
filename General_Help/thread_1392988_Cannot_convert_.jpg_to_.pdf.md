---
title: "Cannot convert .jpg to .pdf"
date: 2010-01-28
forum: General Help
---

### Post by Nexusx6 on 2010-01-28
Hello,

I'm having a heck of a problem getting a large number of photo scanned documents converted into a pdf or djvu. I've pretty much given up on getting them into a djvu file, but now I can't do pdf either.

I'm using convert to try to get them converted into pdf, but after sometime (I don't know how long exactly, I always leave for atleast an hour before I check again) the terminal spits out "Bus error" as an error, and Dolphin will have crashed without an error; I'll come back to find the taskbar gone, and my desktop completely black, though all programs are still running.

This is exactly whats going on:
```
convert *.jpg -adjoin document.pdf
Bus error

```

Any help?

---

### Post by kaibob on 2010-01-28
Imagemagick's convert utility has ongoing problems when converting a large number of image files. The best solution--which was mentioned in another thread on this issue--is to use the graphicsmagick program instead. It's in the repo's, and only takes about 8 MB of disk space. Also, it uses the same command-line syntax except it is preceded by gm. Thus

```
gm convert *.jpg -adjoin -compress JPEG document.pdf
```

For more information on graphicsmagick see:

[http://www.graphicsmagick.org/](http://www.graphicsmagick.org/)

---

### Post by Nexusx6 on 2010-02-01
I know its a little late, but I had to test the hell out of everything before I knew I had no more questions :)

Thanks for the reply, gm works great.

For the sake of future generations who might also run into a "bus error" from either imagemagick or graphicsmagick (I got a bus error from gm in the end), I finally found out what's causing it, and how to fix it.

A bus error is returned (atleast, in my case) when gm or imagemagick run out of space to shove temp files to. This was happening to me because on my set up, root and home are on different partitions. The way to tell either im or gm to use a tmp folder on a larger hard drive or partition is to make a tmp directory on the larger section and point at it with

```

 export MAGICK_TMPDIR=/my/big/directory
```

An there you go.

---

