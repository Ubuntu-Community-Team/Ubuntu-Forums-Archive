---
title: "libtheora.so.0 not found"
date: 2011-08-15
forum: General Help
---

### Post by arch0njw on 2011-08-15
I'm trying to run some software that apparently depends on this.  I have the following theora packages installed:


ii  ffmpeg2theora                              0.24-2build2                                    Theora video encoder using ffmpeg
ii  libtheora-bin                              1.1.1+dfsg.1-3                                  The Theora Video Compression Codec (example 
ii  libtheora-dev                              1.1.1+dfsg.1-3                                  The Theora Video Compression Codec (developm
ii  libtheora0                                 1.1.1+dfsg.1-3                                  The Theora Video Compression Codec

The error message is:


/usr/lib/games/ufoai/ufo: error while loading shared libraries: libtheora.so.0: cannot open shared object file: No such file or directory


I installed this using the i386 debs because there are not 64-bit debs.  Do I need to link that 'so' file somewhere?

---

### Post by arch0njw on 2011-08-18
No solution yet.

After a little investigation, /usr/lib32 does not have a libtheora.so.0 in it.  I suspect I may need to compile this software under 64-bit unless anyone has a bit of wisdom they can share.  (My last attempt to compile this was ... ugly...)

---

