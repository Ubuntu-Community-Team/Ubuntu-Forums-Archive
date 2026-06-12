---
title: "Is there a way to make Beagle search only by filename"
date: 2010-10-06
forum: General Help
---

### Post by sashoalm on 2010-10-06
I'm using Beagle for my desktop search, but sometimes I want to search by a filename only. I can't find an option for that.

---

### Post by ridgeland on 2010-10-06
I use the command line.
$ find /Data/Writer/* -iname '*beagle*'
That finds any file in /Data/Writer or it's sub-directories that has beagle or Beagle or BEAGLE etc.

---

