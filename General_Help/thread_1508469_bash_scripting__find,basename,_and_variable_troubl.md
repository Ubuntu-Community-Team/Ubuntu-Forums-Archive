---
title: "bash scripting : find,basename, and variable trouble"
date: 2010-06-13
forum: General Help
---

### Post by d3v1150m471c on 2010-06-13
Here is my problem. I wrote and am still developing a small program to convert all the videos in a specific input folder to a certain format in an output folder via ffmpeg to go on an Apple Ipod. For the most part, it works well. However, one of the challenges I've encountered is that some videos will not convert due to varied parameter problems. FFmpeg, on the other hand, will still try to create the new video and leave a zero byte file in the output folder. The part I am having trouble with is that **since the outfile has the same name as the input file sans extension** i'd like to use find (or a better command if you can think of one) to get the basename of the zero byte sized file then exec a modified ffmpeg command for each matching video in the original input folder so those videos can actually get converted.  lol here's hoping that makes any sense. Thanks in advance.

IE:
```

find ~/output/* -size 0c -exec ffmpeg -i ~/input/`basename {} .m4v`.* ~/output/`basename {}` \;

```...if only life were ^ easy

---

### Post by d3v1150m471c on 2010-06-13
yay...got it. If anyone wants to know:

```

for i in `find ~/output/* -size 0c`
   do
      ffmpeg ~/input/`basename "$i" .m4v`.* ~/output/`basename "$i"`
  done

```

---

