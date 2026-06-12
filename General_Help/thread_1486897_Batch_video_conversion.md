---
title: "Batch video conversion"
date: 2010-05-18
forum: General Help
---

### Post by hambone79 on 2010-05-18
I have about 50GB of .MOD video files that I need to compress to a smaller format. The only problem is that there are many files (30 second to 5 minute clips) spread out across several directories. I was wondering if anyone knew of a tool that will recursively search the directories and batch convert all of the files? I'm open to anything including a good script for mencoder or ffmpeg.

---

### Post by philinux on 2010-05-18
Moved to general help.

---

### Post by hambone79 on 2010-05-18
I should also point out that I need to do this without a GUI. I will be doing the batch conversion on a server that doesn't have GUI (or monitor) setup on it.

---

### Post by FakeOutdoorsman on 2010-05-18
Using FFmpeg with the *find* command is what I usually use.  Here's an example that will encode all .avi files in the current directory to .mkv files into a directory called *encodes*:
```
find . -name "*.avi" -exec basename \{\} .avi \; | xargs -i ffmpeg -i \{\}.mkv -acodec libfaac -aq 100 -vcodec libx264 -vpre fast -crf 24 -threads 0 encodes/\{\}.mkv
```
Probably could be made recursive fairly easily.  Take a look at [Linux Basics: A gentle introduction to 'find'](http://ubuntuforums.org/showthread.php?t=1128937) for a good start.

---

