---
title: "Unable to update software or install codecs."
date: 2011-08-14
forum: General Help
---

### Post by alittlemorered on 2011-08-14
I've been an ubuntu user for several years and just installed kubuntu 11.4 this morning. Nice desktop and feel. Easily navigable. I like. But i can't download any packages!

When i try "check for new updates" in KPackageKit i get:
"
W: Failed to fetch gzip:/var/lib/apt/lists/partial/mg.archive.ubuntu.com_ubuntu_dists_natty_main_bina ry-i386_Packages Hash Sum mismatch
E: Some index files failed to download. They have been ignored, or old ones used instead.
"

When i try installing media codecs in amarok or dragon, i get responses like:
"
another package manager is open (which shouldn't be the case as i've just logged in)
"
or
"
The following packages have unmet dependencies:
gstreamer0.10-plugins-ugly: Depends: libcdio10 but it is not installable
Depends: libid3tag0 (>= 0.15.1b) but it is not installable
Depends: libmad0 (>= 0.15.1b-3) but it is not installable
gstreamer0.10-ffmpeg: Depends: libavcodec52 (>= 4:0.6-1~) but it is not installable or
libavcodec-extra-52 (>= 4:0.6-1~) but it is not going to be installed
Depends: libavformat52 (>= 4:0.6-1~) but it is not installable or
libavformat-extra-52 (>= 4:0.6-1~) but it is not going to be installed
Depends: libavcodec52 ( libavcodec-extra-52 ( gstreamer0.10-plugins-bad: Depends: libass4 (>= 0.9.7) but it is not going to be installed
Depends: libdc1394-22 but it is not installable
Depends: libdirectfb-1.2-9 but it is not installable
Depends: libflite1 but it is not installable
Depends: libgsm1 (>= 1.0.13) but it is not installable
Depends: libmusicbrainz4c2a (>= 2.1.5) but it is not installable
Depends: libofa0 (>= 0.9.3) but it is not installable
Depends: librsvg2-2 (>= 2.26.0) but it is not installable
Depends: libschroedinger-1.0-0 (>= 1.0.9) but it is not installable
Depends: libvpx0 (>= 0.9.0) but it is not installable
"

Over the years i've used "http://ubuntuforums.org/showthread.php?t=766683" to update my system but i get no joy this time.

I'm using kubuntu 11.4 on a fujitsu-siemens amillo pi2530. I've enable the natty universe and multiverse repositries.

Regards,
Red

---

### Post by wojox on 2011-08-14
Try a different mirror from Software Sources.

---

### Post by alittlemorered on 2011-08-15
Solved. Thank you so much! 

The option is a little less obvious in kubuntu, tucked away under 'origins'.

---

