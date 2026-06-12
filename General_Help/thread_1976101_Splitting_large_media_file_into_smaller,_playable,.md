---
title: "Splitting large media file into smaller, playable, bits."
date: 2012-05-08
forum: General Help
---

### Post by carranty on 2012-05-08
I have a TV that has a built in media player.  I plug in a FAT formatted USB stick and can then play any media file on the stick.  I have an 8.7GB mkv file I'd like to play on it however I can only fit a 4GB file onto it (due to it being formatted in FAT).  How can I split the 8.7GB file into smaller <4GB files.  I've tried using split and lxsplit but the split parts aren't playable.  I need the split files to be playable media files in their own right or else I can't play them on the TV.  I also tried mencoder like in the below link but this created a very jittery file that froze when I tried to skip forward (the original file is not jittery and does not freeze).

[HTML]http://ubuntuliving.blogspot.co.uk/2008/03/splitting-avi-file-into-smaller-parts.html[/HTML]

Has anyone any suggestions?

---

### Post by ron999 on 2012-05-08
> **carranty said:**
> I have an 8.7GB mkv file I'd like to play on it however I can only fit a 4GB file onto it...
Has anyone any suggestions?
Hi
mkvmergeGUI will do the job.
Look at post #7 here ---> [http://ubuntuforums.org/showthread.php?t=1958361]("http://ubuntuforums.org/showthread.php?t=1958361")
Also, with command line, see here ---> [http://www.bunkus.org/videotools/mkvtoolnix/doc/mkvmerge.html#mkvmerge.description.split]("http://www.bunkus.org/videotools/mkvtoolnix/doc/mkvmerge.html#mkvmerge.description.split")

---

### Post by carranty on 2012-05-08
Just what I was looking for.  Thanks.

---

