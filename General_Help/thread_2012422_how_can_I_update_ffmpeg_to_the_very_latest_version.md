---
title: "how can I update ffmpeg to the very latest version"
date: 2012-06-29
forum: General Help
---

### Post by p3aul on 2012-06-29
Ubuntu 10.04
Gnome 2
Nautulus 2.30.1

I have ffmep .4 something and I want to update to .6 or above How can I do this?
Thanks,
Paul

---

### Post by ron999 on 2012-06-29
> **p3aul said:**
> 

I have ffmep .4 something and I want to update to .6 or above...
Hi
The way to do this is compile latest FFmpeg from GIT.

For Ubuntu 10.04 the guide is here ---> [https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuideLucid]("https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuideLucid")

---

### Post by p3aul on 2012-06-29
I have an awful feeling that something is going to go wrong. How can I keep my original installation safe from harm? The first thing that site says do is to remove the old installation.

---

### Post by FakeOutdoorsman on 2012-06-29
> **p3aul said:**
> I have an awful feeling that something is going to go wrong. How can I keep my original installation safe from harm? The first thing that site says do is to remove the old installation.

The guide ron999 linked to has a section called "Reverting Changes Made by This Guide" at the bottom of the page. You can then re-install the version from the repository and any dependencies that may have been removed. See */var/log/dpkg.log* for a record of removed packages.

I have plans to create a "local installation" version of the guide that will allow both the repo ffmpeg and compiled ffmpeg to co-exist.

---

