---
title: "Can you still locate and save streaming video files in cache?"
date: 2012-05-28
forum: General Help
---

### Post by Manmadegod on 2012-05-28
I did this a few years ago while running Windows, and it seemed a bit more straightforward. Not that I blame Linux for that.

Even if there was a decent program available for saving non-YouTube streaming video (I would like to save streams from Nowvideo, Putlocker, Videoweed, Vidbux, Vidxden, Movshare, etc), it would not work with them all, and if a program can find them, then I should be able to as well. But the information which I've read isn't consistent with what I have (not) found after setting Thunar to display all hidden files. The question is where are they being held now while downloading?

Sometime last year, somebody did a how-to for Linux (can there really be a difference with Xubuntu?), and stated that it was easy to find stream-downloaded videos in the /tmp folder, which can be renamed and saved on your actual hard disk.  According to his information, I should find here some  growing files (as files download from their host sites) with names beginning with "flash", but I have not found this to be the case. So far I've found nothing which appears to be any type of video file, while I do have video streams from fairly popular sites (but not YouTube) in progress. Does anyone know what's up with the elusive nature of streamed files now, or where they may actually be found in Xubuntu?

Thanks.

---

### Post by pqwoerituytrueiwoq on 2012-05-28
depends on the source some work some don't
find the video:
```
f="$(ls -l /proc/$(pgrep -f flashplayer)/fd | grep deleted)" && f="${f##*:+([0-9]) }" && f="${f%% -*}" && echo /proc/$(pgrep -f flashplayer)/fd/"$f"
```then you copy the file it gives you to where ever you want it
i usually junk symlink to it and play it in smplayer for hardware acceleration

---

### Post by Manmadegod on 2012-05-28
> **pqwoerituytrueiwoq said:**
> depends on the source some work some don't
find the video:
```
f="$(ls -l /proc/$(pgrep -f flashplayer)/fd | grep deleted)" && f="${f##*:+([0-9]) }" && f="${f%% -*}" && echo /proc/$(pgrep -f flashplayer)/fd/"$f"
```then you copy the file it gives you to where ever you want it
i usually junk symlink to it and play it in smplayer for hardware acceleration

Thanks, it almost works! Problems are that I am, for the first time ever, unsure how to copy something.  Your command did yield a file or link,  with a video icon, and it actually played from where I navigated to it, in  /proc/19674/fd/21.  But I'm not clear on this being anything other than a link file (that's what it says in the Properties window).  When I copy it to my /home/me/Downloads file, it copies something entirely different, which is unlike anything which I have seen before! It doesn't really appear to be anything other than an icon in my Downloads folder, the type is "unknown" in it's Properties window, and of course it can't be played. What do I need to do to fix this?

---

### Post by pqwoerituytrueiwoq on 2012-05-29
```
d="`date`";ln -s `f="$(ls -l /proc/$(pgrep -f flashplayer)/fd | grep deleted)" && f="${f##*:+([0-9]) }" && f="${f%% -*}" && echo /proc/$(pgrep -f flashplayer)/fd/"$f"` /tmp/"movie-$d";totem /tmp/"movie-$d"
```
that will make a link in /tmp and open the video in totem
i know this works on putlocker used to work on youtube

---

### Post by Manmadegod on 2012-05-29
> **pqwoerituytrueiwoq said:**
> ```
d="`date`";ln -s `f="$(ls -l /proc/$(pgrep -f flashplayer)/fd | grep deleted)" && f="${f##*:+([0-9]) }" && f="${f%% -*}" && echo /proc/$(pgrep -f flashplayer)/fd/"$f"` /tmp/"movie-$d";totem /tmp/"movie-$d"
```that will make a link in /tmp and open the video in totem
i know this works on putlocker used to work on youtube

That does what it's supposed to, but the problem is that we're still talking links. I want to save the target file to my hard drive, and I still cannot find a way of doing that.  What I get after running your first formula under the /proc/****/fd folder is regarded by my system as a link, not a file, and will not even copy to my hard disk as a link.  I can find no way of saving the target file from here,  even though I know there must be a savable file somewhere in my cache.  Totem has not offered to save it from the menu either. 

The last time I succeeded in saving streamed vids as files was a few years ago, while I was running Windows XP.  It was as basic as finding the \tmp folder somewhere under Mozilla, where downloaded videos didn't pretend to be otherwise (just rename them), and they were easily sorted out by their file extensions - therefore, this all has me super-confused!  I am open to the notion that streaming sites and systems may be different now, not to blame Linux for being the big PIA about it. But what is it that I have to do to get an actual copy of what I have streamed to my computer, rather than just a link to it wherever?

---

### Post by nothingspecial on 2012-05-30
Please read this

[http://ubuntuforums.org/showthread.php?t=1850955](http://ubuntuforums.org/showthread.php?t=1850955)

The same applies for movshare, videoweed etc

---

