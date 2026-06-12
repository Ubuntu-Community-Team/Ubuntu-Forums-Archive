---
title: "create dvd with a movie as the bg 'Q' DVD-Author"
date: 2010-03-23
forum: General Help
---

### Post by lindylex on 2010-03-23
I am trying to create a dvd with a movie as the background but I keep getting the same errors and no dvd files are being created.  Below are the errors I receive from running the .sh file that 'Q' DVD-Author generates.


jpeg: /tmp/acrobatic_yoga_dvd_volume_1/Main Menu VMGM/background - Output directory already exists and is writable.
V: 104.0 3117/3117  9% 47%  0.0% 0 0

Exiting... (End of file)
#=- Internal : Render Menu -=# Main Menu VMGM
   INFO: [png2yuv] Parsing & checking input files.
PNG file open failed:: No such file or directory
**ERROR: [png2yuv] Reading of /tmp/acrobatic_yoga_dvd_volume_1/Main Menu VMGM/background/rendered_00000001.png failed.

   INFO: [mpeg2enc] SETTING EXTENDED MMX for MOTION!
   INFO: [mpeg2enc] SETTING SSE and MMX for TRANSFORM!
   INFO: [mpeg2enc] SETTING EXTENDED MMX for PREDICTION!
**ERROR: [mpeg2enc] Could not read YUV4MPEG2 header: system error (failed read/write)!
   INFO: [mplex] mplex version 1.8.0 (2.2.4 $Date: 2005/08/28 17:50:54 $)
**ERROR: [mplex] Unable to open file /tmp/acrobatic_yoga_dvd_volume_1/Main Menu VMGM/menu.m2v for reading.
./script_for_dvd.sh: line 93: /tmp/acrobatic_yoga_dvd_volume_1/Main Menu VMGM/menu.mpg: No such file or directory
DVDAuthor::dvdauthor, version 0.6.14.
Build options: gnugetopt magick iconv freetype
Send bugs to <dvdauthor-users@lists.sourceforge.net>

./script_for_dvd.sh: line 105: 18995 Segmentation fault      /usr/bin/dvdauthor -x "/tmp/acrobatic_yoga_dvd_volume_1/dvdauthor.xml"

---

