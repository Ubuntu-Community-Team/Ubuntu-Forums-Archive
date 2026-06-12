---
title: "Ubuntu 11.04 unable to install programs"
date: 2011-08-14
forum: General Help
---

### Post by RoseForTheApocalypse on 2011-08-14
hi, am very new to linux, and i just installed the latest linux 11.04 and i want to install flash player and vlc so i can use the internet and watch music, videos with vlc. but the thing is when i tried installing adobe flash player from the Ubuntu Software Center i got an error which goes like this:
A windows pops up when i click the button install.
(but i managed to install wine from to terminal)

An unhandlable error occured
There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks.

Details
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 961, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1085, in _simulate_helper
    return depends, self._cache.required_download, \
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 226, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the ttf-mscorefonts-installer package. This might mean you need to manually fix this package.

Also the os is freshly installed, with no problems, am running it on acer laptop TravelMate 2493WLMi
intel 1.7Ghz, 512 Mb ram DDR2 pretty old but solid laptop
any help would be appreciated, thanks. :confused:

---

### Post by Freezing on 2011-08-14
click the power button, go to system settings, scroll down to synaptic package manager once it opens, in the left corner click mark all upgrates and click apply then it will automaticly download them and install them all you have to do is sit right back and ejoy the ride, am 100% positive it will fix your problem :)

---

### Post by RoseForTheApocalypse on 2011-08-14
hey man, thanks for the help, i just updated my os and everything works like a charm.
thanks alot again :)

---

### Post by alittlemorered on 2011-08-14
Hi RoseForTheApocalypse. 

Sorry that i can't help, but I have a very similar thing with Kubuntu 11.4. I've been an ubuntu user for several years and just installed kubuntu 11.4 this morning. Nice desktop and feel. Easily navigable. I like. But i can't download any software!

When i try "check for new updates" in KPackageKit i get:
"
W: Failed to fetch gzip:/var/lib/apt/lists/partial/mg.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages Hash Sum mismatch
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

