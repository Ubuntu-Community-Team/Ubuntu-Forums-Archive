---
title: "Run script on CD/DVD ejection?"
date: 2011-07-07
forum: General Help
---

### Post by wkulecz on 2011-07-07
Is it possible to run a script when a CD/DVD is ejected using the desktop icon context menu?

I'm using avidemux2 on 10.04 as a video frame server via a plugin I wrote for some interactive video image processing.  The source video are on DVD-R recorded with a commercial stand alone DVD Recorder box.

Everything works well except, to read the DVD-R VOB files avidemux2 creates an index files in /temp.  The problem is when the DVD is ejected and the next one inserted avidemux2 is smart enough to detect the change and offers to rebuild the index files, but it crashes when rebuilding the index files :(

If I delete the index files after ejecting the DVD everything works fine the next time.  So if I could hook a simple script into the context menu eject function I could automate the process simplifying the life of my end users.

---

### Post by wkulecz on 2011-07-08
Bump.

Is there a better forum to ask this question?

---

