---
title: "Kino to RealMedia"
date: 2006-03-29
forum: General Help
---

### Post by Lary Grant on 2006-03-29
I'm trying to get from Kino to RealMedia.  As I posted earlier, Kino crashes when I try to export an AVI file.  I can export a DV file and then run

ffmpeg -i foo.dv foo.rm

but RealPlayer won't play that file.  It says:

The content you are trying to play uses an audio codec that is obsolete and no longer supported. Please contact the content provider about using a supported codec.

Another thing I tried was;

ffmpeg -i foo.dv foo.avi
producer -i foo.avi -o foo.rm

but I get 

Error: Failure to load reader for file foo.avi

---

