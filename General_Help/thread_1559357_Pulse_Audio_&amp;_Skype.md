---
title: "Pulse Audio &amp; Skype"
date: 2010-08-23
forum: General Help
---

### Post by ngrieb on 2010-08-23
I have been trying to get skype working on 10.04 x64. I succeeded last night by using a pulseaudio config file to stop autospawning, but this kills volume management on many other apps as well. I just wrote a quick skype startup script to kill pulseaudio when skype is opened, and replace it when skype is closed, but I would rather have an autospawning exception for skype only. Is there a way to tell pulse audio not to autospawn for skype related processes only?

---

### Post by ngrieb on 2010-08-29
Gee, no one the whole time? I figured out that it was pulseaudio's autospawning functionality that messes with the skype audio. The easiest fix for me was simply killing pulse via pulseaudio -k before and re-enabling it after via pulseaudio -D.
I just wrote a shell script to run these functions when I use the desktop launcher. Hope this helps someone else out there.
[SOLVED]

---

