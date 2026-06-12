---
title: "gstreamer update for mp3's on Amarok"
date: 2006-03-08
forum: General Help
---

### Post by Coulrophobe on 2006-03-08
What the heck is all this ?

I ran
sudo apt-get install gstreamer0.8-plugins gstreamer0.8-lame gstreamer0.8-ffmpeg gstreamer0.8-plugins-multiverse gst-register-0.8 in a term
but this is the results

Setting up gstreamer0.8-a52dec (0.8.11-0ubuntu5) ...
OIL: ERROR liboiltest.c 247: (): illegal instruction in idct8x8_s16_mmx
OIL: ERROR liboiltest.c 247: (): illegal instruction in idct8x8_s16_mmx

Setting up gstreamer0.8-aa (0.8.11-0ubuntu5) ...
OIL: ERROR liboiltest.c 247: (): illegal instruction in idct8x8_s16_mmx
OIL: ERROR liboiltest.c 247: (): illegal instruction in idct8x8_s16_mmx

Setting up gstreamer0.8-artsd (0.8.11-0ubuntu5) ...
OIL: ERROR liboiltest.c 247: (): illegal instruction in idct8x8_s16_mmx
OIL: ERROR liboiltest.c 247: (): illegal instruction in idct8x8_s16_mmx

Setting up gstreamer0.8-caca (0.8.11-0ubuntu5) ...
OIL: ERROR liboiltest.c 247: (): illegal instruction in idct8x8_s16_mmx
OIL: ERROR liboiltest.c 247: (): illegal instruction in idct8x8_s16_mmx

Setting up libcdio3 (0.71-2ubuntu2) ...

Setting up gstreamer0.8-cdio (0.8.11-0ubuntu5) ...
OIL: ERROR liboiltest.c 247: (): illegal instruction in idct8x8_s16_mmx
OIL: ERROR liboiltest.c 247: (): illegal instruction in idct8x8_s16_mmx

Setting up libdirac0 (0.5.2-0ubuntu1) ...

Setting up gstreamer0.8-dirac (0.8.11-0ubuntu1) ...
OIL: ERROR liboiltest.c 247: (): illegal instruction in idct8x8_s16_mmx
OIL: ERROR liboiltest.c 247: (): illegal instruction in idct8x8_s16_mmx

Setting up libmp4v2-0 (2.0.0+cvs20040908+mp4v2+bmp-0ubuntu2) ...

Setting up libfaac0 (1.24clean-0ubuntu3) ...

Setting up gstreamer0.8-faac (0.8.11-0ubuntu1) ...
OIL: ERROR liboiltest.c 247: (): illegal instruction in idct8x8_s16_mmx
OIL: ERROR liboiltest.c 247: (): illegal instruction in idct8x8_s16_mmx

Setting up libfaad2-0 (2.0.0+cvs20040908+mp4v2+bmp-0ubuntu2) ...

Setting up gstreamer0.8-faad (0.8.11-0ubuntu1) ...
OIL: ERROR liboiltest.c 247: (): illegal instruction in idct8x8_s16_mmx
OIL: ERROR liboiltest.c 247: (): illegal instruction in idct8x8_s16_mmx

Setting up gstreamer0.8-festival (0.8.11-0ubuntu5) ...
OIL: ERROR liboiltest.c 247: (): illegal instruction in idct8x8_s16_mmx
OIL: ERROR liboiltest.c 247: (): illegal instruction in idct8x8_s16_mmx

Setting up gstreamer0.8-ffmpeg (0.8.6-0ubuntu3) ...
OIL: ERROR liboiltest.c 247: (): illegal instruction in idct8x8_s16_mmx
OIL: ERROR liboiltest.c 247: (): illegal instruction in idct8x8_s16_mmx

Setting up gstreamer0.8-gtk (0.8.11-0ubuntu5) ...
OIL: ERROR liboiltest.c 247: (): illegal instruction in idct8x8_s16_mmx
OIL: ERROR liboiltest.c 247: (): illegal instruction in idct8x8_s16_mmx

Setting up liblame0 (3.96.1-1) ...

Setting up gstreamer0.8-lame (0.8.11-0ubuntu1) ...
OIL: ERROR liboiltest.c 247: (): illegal instruction in idct8x8_s16_mmx
OIL: ERROR liboiltest.c 247: (): illegal instruction in idct8x8_s16_mmx

Setting up libid3tag0 (0.15.1b-7) ...

Setting up libmad0 (0.15.1b-2.1) ...

Setting up gstreamer0.8-mad (0.8.11-0ubuntu5) ...
OIL: ERROR liboiltest.c 247: (): illegal instruction in idct8x8_s16_mmx
OIL: ERROR liboiltest.c 247: (): illegal instruction in idct8x8_s16_mmx

Setting up libmikmod2 (3.1.11-a-6ubuntu2) ...

Setting up gstreamer0.8-mikmod (0.8.11-0ubuntu5) ...
OIL: ERROR liboiltest.c 247: (): illegal instruction in idct8x8_s16_mmx
OIL: ERROR liboiltest.c 247: (): illegal instruction in idct8x8_s16_mmx

Setting up libmms0 (0.1-0ubuntu1) ...

Setting up gstreamer0.8-mms (0.8.11-0ubuntu5) ...
OIL: ERROR liboiltest.c 247: (): illegal instruction in idct8x8_s16_mmx
OIL: ERROR liboiltest.c 247: (): illegal instruction in idct8x8_s16_mmx

Setting up libmpeg2-4 (0.4.0b-2ubuntu4) ...

Setting up gstreamer0.8-mpeg2dec (0.8.11-0ubuntu5) ...
OIL: ERROR liboiltest.c 247: (): illegal instruction in idct8x8_s16_mmx
OIL: ERROR liboiltest.c 247: (): illegal instruction in idct8x8_s16_mmx

Anyone advise ?

S

---

### Post by 11hjpphty76lkjj on 2006-03-08
Is your default language not english?  Just curious because when I search for this sort of error message with google I find a lot of (what appears to me to be) french conversation about this sort of error, but not much english.  Have you tried removing the offending packages and then re-installing?

Aaron

---

