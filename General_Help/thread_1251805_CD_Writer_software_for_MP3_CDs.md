---
title: "CD Writer software for MP3 CDs"
date: 2009-08-28
forum: General Help
---

### Post by BFG on 2009-08-28
My car audio can play MP3 CDs, which is great.  It also plays from a USB stick.

Simple MP3 players will often play files in the order they are stored on the media (ls -lU shows this), ignoring filenames and ID3 tags.
[http://www.murraymoffatt.com/software-problem-0010.html](http://www.murraymoffatt.com/software-problem-0010.html)
This can be easily fixed on USB using something like this script:
[http://www.linuxforums.org/forum/linux-newbie/111044-change-order-files-directory.html](http://www.linuxforums.org/forum/linux-newbie/111044-change-order-files-directory.html)

BUT ON CD.....
On windows, nero and some other software packages have a setting for MP3 CD, which creates a data CD, but pays extra attention to the file system order.

I've found that the main offerings on Ubuntu for burning CDs don't offer this level of control.  Can anyone recommend some software that can do this?

---

### Post by HiImTye on 2009-08-28
Brasero *should* do this if I recall correctly, been a while since I used it

just make sure that the 'normalize' plugin is disabled, it causes lots of problems

---

### Post by BFG on 2009-08-28
I'll give that a try - thanks!

---

### Post by P4man on 2009-08-28
It would surprise you if there wouldnt be an opensource app to do that, but if all else fails, know that nero also exists for linux:

[http://www.nero.com/eng/linux3.html](http://www.nero.com/eng/linux3.html)

---

### Post by HiImTye on 2009-08-28
yeah but nero for linux is a joke, it's like a five year old version of nero (or at least functions as one)

---

### Post by mcduck on 2009-08-28
Any CD-burning app will bur "MP3-CD"s. They are just normal data-CD's with MP3 files in them.

Just select "Data-CD" and add your MP3 files. That's all. No special software needed.

---

### Post by BFG on 2009-08-28
> **mcduck said:**
> Any CD-burning app will burn "MP3-CD"s. 
Nope.  The needs for burning an MP3 CD are subtly different.  The data is idenitical, but the order in which files are burnt to the disc is significant. A Data CD doesn't care, and will burn the files on in the same order that they are stored on the source hard drive.

The problem with normal data is that the files are created in order of hash count or something like that.
Just look at any mp3 album on your hard drive and list using:
ls -lU

This will list the tracks in file system order, which is "normal data".  As you will see "Normal data" order is not the same as filename order.


> **mcduck said:**
> 
They are just normal data-CD's with MP3 files in them.

You are right, the data CD will be indistinguishable from any other data CD, the difference only occurs in the burning software at the time of burning.

Done properly, the end result can be mounted and ls -Ul output should be identical to ls -l. :)

> **HiImTye said:**
> Brasero *should* do this if I recall correctly, been a while since I used it

just make sure that the 'normalize' plugin is disabled, it causes lots of problems

That seems to work!  First disc burnt is in the right order - Thanks! :)

---

