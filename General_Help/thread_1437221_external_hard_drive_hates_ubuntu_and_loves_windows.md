---
title: "external hard drive hates ubuntu and loves windows"
date: 2010-03-23
forum: General Help
---

### Post by balta on 2010-03-23
Hi there!
I got a really weird case here:

**Situation**
I have got an external multimedia box, it has an internal hard drive (samsung 750GB) and a case which can be connected to a TV to view movies and pictures and listen to music.
I had it for years and it never gave me a single problem, recently I had some [issues ]("http://ubuntuforums.org/showthread.php?t=1358317")but, helped by the ubuntu community, I managed to backup all the data after reformatting it.
I have always used it with ubuntu (since 7.04) and windows, obviously I could see all the files in it no matter which system I were using .

**Problem**
The weird part is this: when I attach the thing to the TV the box can now (never had this problem in past) view only the files I moved into the hard drive under windows, if I copy a file using ubuntu it will not see it, even the very same file... I tried two different computers, in both only the files moved there using windows (XP in both cases) where recognized, the ones using ubuntu (9.10 in both cases) where just absolutely ignored, as if they had never existed BUT I can see all the files under any OS.

**What I tried**
I already tried reformatting it many (really many) times, under ubuntu and windows, and to different filesystems (NTFS - FAT32 - FAT16) the results were always the same, the box would only recognize the files I moved on under windows...

Soooo, what can I do to make the thing work as it had alway done?
I do really can't see any logic reason why the box can't see the files I move in it from ubuntu... please help me, I don't want to be slayed under microsoft :(


PS: the box don't recognize any kind of file moved in it under ubuntu, even more strange is the fact that it recognizes folders in a really random way as it sometimes see them sometimes no (of course all folder copied or created under windows are perfectly recognized)

PPS: I tried copying into it a file under ubuntu and then moving it under windows, the box got quite angry and stopped recognizing all files that were in the same branch of folders O.o

Tell me it is not gone forever and forgive me for this looooong post :D

---

### Post by Elwro on 2010-03-24
I guess I won't be of any help, but perhaps you'd consider this: I had problems with Ubuntu and a big ntfs partition which resulted in folders "disappearing" from default view in windows. Turned out that sometimes folders Ubuntu was operating on ended up having the "hs" attributes (hidden / system), and so you had to specifically tell Windows to see them. So, perhaps there's something wrong with folder attributes?

---

