---
title: "Joining a bunch of avi files that are in a set sequence"
date: 2011-07-27
forum: General Help
---

### Post by p3aul on 2011-07-27
I Need help to join about 8 avi files the filenames are in the format "blah.avi.001", blah.avi.002, blah.avi,003 blah.avi.004 etc. I want them joined so there is just one avi file. How can I do this?
Thanks,
Paul

---

### Post by mikewhatever on 2011-07-28
I've used mencoder (install from the repositories) to do it. Renaming the parts to p1.avi, p2.avi, etc makes for less typing, but you don't have to. I've looked up the options in 'man mencoder', but quite honestly, don't remember what they are now. You are welcome to check yourself.
```
mencoder -forceidx -ovc copy -oac copy -o output.avi p1.avi p2.avi p3.avi
```

---

### Post by p3aul on 2011-07-28
Well I did as you suggested but was unsuccessful. here is the output from memcoder:

> p3aul@p3aul-Aspire-X3910:/media/My Book/video/video$ mencoder -forceidx -ovc copy -oac copy -o output.avi p1.avi p2.avi p3.avi p4.avi p5.avi p6.avi p7.avi p8.avi
MEncoder 1.0rc4-4.5.2 (C) 2000-2010 MPlayer Team
success: format: 0  data: 0x0 - 0x5f00000
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
AVI: Generated index table for 37734 chunks!
VIDEO:  [XVID]  544x272  12bpp  23.976 fps  881.4 kbps (107.6 kbyte/s)
[V] filefmt:3  fourcc:0x44495658  size:544x272  fps:23.976  ftime:=0.0417
videocodec: framecopy (544x272 12bpp fourcc=44495658)
audiocodec: framecopy (format=55 chans=2 rate=48000 bits=0 B/s=16000 sample-384)
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
success: format: 0  data: 0x0 - 0x5f00000:   0min 717mb  A-V:0.042 [881:127]
Seek failed
============ Sorry, this file format is not recognized/supported =============
=== If this file is an AVI, ASF or MPEG stream, please contact the author! ===
Cannot open demuxer.

Exiting...
p3aul@p3aul-Aspire-X3910:/media/My Book/video/video$ 

Say, there really isn't a smily face up there in that code! that's just what to Ubuntu forum processor equated it to! :P

Apparently, memcoder doesn't "do" avi files:(

Thanks,
Paul

---

### Post by HermanAB on 2011-07-28
Try ffmpeg.

---

### Post by mikewhatever on 2011-07-28
Wish I new what's wrong. It worked very well for me, except once when the two parts had different aspect ratios.

---

### Post by satish_j on 2011-07-28
> **p3aul said:**
> I Need help to join about 8 avi files the filenames are in the format "blah.avi.001", blah.avi.002, blah.avi,003 blah.avi.004 etc. I want them joined so there is just one avi file. How can I do this?
Thanks,
Paul

You can use,from terminal:
```

cat avi.001 avi.002 avi.003........>FinalFile.avi

```

---

### Post by mikewhatever on 2011-07-28
> **satish_j said:**
> You can use,from terminal:
```

cat avi.001 avi.002 avi.003........>FinalFile.avi

```

Did it work for you?
I've seen many people posting it as a solution, tried it and it did absolutomente nada.

---

### Post by satish_j on 2011-07-28
> **mikewhatever said:**
> Did it work for you?
I've seen many people posting it as a solution, tried it and it did absolutomente nada.

i have been using it from last 3 yrs to merge the 001,002... files downloaded from internet..:P

---

### Post by mikewhatever on 2011-07-28
Hope it works for the OP.

---

### Post by p3aul on 2011-07-28
I'm fixing to find out:)

I will try this but I think this just concatenates the files. I don't believe it's that easy, but I'm willing to try
Paul

---

### Post by 4Orbs on 2011-07-28
If you have already installed ffmpeg then just use avimerge in a terminal:
```
avimerge -o /path_and_name/of_finished_video.avi -i /path_and_names/of_pieces_to_merge_01.avi /path_and_names/of_pieces_to_merge_02.avi
```
hit Enter and it will complete very quickly.

---

### Post by p3aul on 2011-07-28
Whoops sorry 4orbs I didn't see your post and I wasn't reffering to it. will try your suggestion now!

Nope didn't work just gave me a bunch of trash in the terminal output for a few minutes. I had a program when I was running Win 7 that would do it, so I know there has to an app with a GUI that will do it for Ubuntu :(

---

### Post by p3aul on 2011-07-28
Well it created a file called finished.avi but Right clicking and selecting properties  just give a msg that it is trying to create "properties" It won't play in the media player either.

---

### Post by yetiman64 on 2011-07-28
> **p3aul said:**
> Whoops sorry 4orbs I didn't see your post and I wasn't reffering to it. will try your suggestion now!

Nope didn't work just gave me a bunch of trash in the terminal output for a few minutes. I had a program when I was running Win 7 that would do it, **so I know there has to an app with a GUI that will do it for Ubuntu** :(Try avidemux from the repos, I use it here to join video part files. Has worked with avi in the past for me. Just make sure the aspect ratios are all the same first (you can use avidemux to alter this as well on individual file parts).

---

### Post by p3aul on 2011-07-28
Ok Thanks. I just tried playing each avi segment. all the files are corrupt! I guess that was my problem all along. Thanks for helping everyone!:P
Paul

---

