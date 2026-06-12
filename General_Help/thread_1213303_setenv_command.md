---
title: "setenv command?"
date: 2009-07-14
forum: General Help
---

### Post by PerfectReign on 2009-07-14
I'm trying to install a program called, Free Surfer - [http://surfer.nmr.mgh.harvard.edu/fswiki/LinuxInstall](http://surfer.nmr.mgh.harvard.edu/fswiki/LinuxInstall)

In the instructions it says to use setenv to setup an environment variable: setenv FREESURFER_HOME /usr/local/freesurfer

I tried this as both my user and su and get a command not found message. Googleling, I found this thread: [http://ubuntuforums.org/showthread.php?t=143962](http://ubuntuforums.org/showthread.php?t=143962) - which suggested to use EXPORT. That's a program I remember on my openSUSE system.

In any case, I am not able to get anywhere. Can someone help?

Oh, and here's teh message I get with export:

kai@r2d2:~/downloads$ export FREESURFER_HOME /usr/local/freesurfer
bash: export: `/usr/local/freesurfer': not a valid identifier

---

### Post by baseface on 2009-07-14
```
export FREESURFER_HOME="/usr/local/freesurfer"
```

---

