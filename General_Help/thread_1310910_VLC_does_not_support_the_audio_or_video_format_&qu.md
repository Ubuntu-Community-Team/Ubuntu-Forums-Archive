---
title: "VLC does not support the audio or video format &quot;h264&quot;. Only sound when playing video."
date: 2009-11-02
forum: General Help
---

### Post by Rytron on 2009-11-02
Hi.
I had installed some packages from Ubuntu-Tweak. That may have caused this problem.

I play a video file and only get sound in vlc. This is the error:
[I]No suitable decoder module:
VLC does not support the audio or video format "h264". Unfortunately there is no way for you to fix this.[/I]

I go to the terminal to install ffmpeg and get this:

```
:~$ sudo apt-get install ffmpeg
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ffmpeg: Depends: libavcodec52 (< 4:0.5+svn20090706-99) but it is not going to be installed or
                   libavcodec-extra-52 (< 4:0.5+svn20090706-99) but 4:0.5+svn20090926-0ubuntu3~tj~ppa1k is to be installed
          Depends: libavdevice52 (>= 4:0.5+svn20090706) but it is not going to be installed or
                   libavdevice-extra-52 (>= 4:0.5+svn20090706) but it is not going to be installed
          Depends: libavdevice52 (< 4:0.5+svn20090706-99) but it is not going to be installed or
                   libavdevice-extra-52 (< 4:0.5+svn20090706-99) but it is not going to be installed
          Depends: libavfilter0 (>= 4:0.5+svn20090706) but it is not going to be installed or
                   libavfilter-extra-0 (>= 4:0.5+svn20090706) but it is not going to be installed
          Depends: libavfilter0 (< 4:0.5+svn20090706-99) but it is not going to be installed or
                   libavfilter-extra-0 (< 4:0.5+svn20090706-99) but it is not going to be installed
          Depends: libavformat52 (< 4:0.5+svn20090706-99) but it is not going to be installed or
                   libavformat-extra-52 (< 4:0.5+svn20090706-99) but 4:0.5+svn20090926-0ubuntu3~tj~ppa1k is to be installed
          Depends: libswscale0 (< 4:0.5+svn20090706-99) but it is not going to be installed or
                   libswscale-extra-0 (< 4:0.5+svn20090706-99) but 4:0.5+svn20090926-0ubuntu3~tj~ppa1k is to be installed
E: Broken packages

```

Please help!

---

### Post by hansdown on 2009-11-02
Howdy Rytron.

The broken package error needs to be fixed.

Open synaptic. 

In the lower, left column, click custom filters.

Click broken, and it should offer an option to fix broken packages.

---

### Post by Rytron on 2009-11-02
Hi hansdown.
There were no entries in the broken packages section!

However just below that, I saw where it said 'Missing Recommends'. I installed some libraries that were in that section. Then I used Totem to open a recently downloaded YouTube video, it did a search for plugins and installed them.

All fixed!

:D

---

### Post by hansdown on 2009-11-02
Glad you fixed it Rytron.

Nice going!

---

