---
title: "DEB wont install on 12.04 - have source code"
date: 2012-05-26
forum: General Help
---

### Post by ddarsow on 2012-05-26
I have a deb file for a program (TXPPM) which ran perfectly on 11.04. It appears to install through the Software Center in 12.04, but will not launch.

I have also tried recompiling from the source code which I have as well, but get errors. It appears to be looking for files on the developers machine?

The output of the make command contains a bunch of errors such as:
```
/home/tomas/Programming/txppm/portaudio/src/hostapi/alsa/pa_linux_alsa.c:2526: undefined reference to `snd_pcm_status_get_delay'

```

the problem seems to be that the user tomas is the dev and the user on by machine is dave. Not sure what is going on with why the deb file does not install or why the compile is breaking???

---

### Post by rai4shu2 on 2012-05-26
The software you are trying to use seems to be inactive. Perhaps you should be emailing the author about your problems?

In any case, errors involving "undefined references" nearly always mean that you need a -dev package or source code for whatever it's related to (in your case, I suspect you need the Linux kernel source code to build your module).

---

