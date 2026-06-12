---
title: "Preventing monitor shutdown in virtual terminal"
date: 2011-11-01
forum: General Help
---

### Post by ManFromMars on 2011-11-01
Howdy,

How can I prevent automatic monitor switch-off (or whatever it's called... when you've been inactive for some minutes and your computer stops sending output to your screen) when I'm in a virtual terminal session, with X stopped? In the Ubuntu desktop settings, I've told it never to switch the screen off, but this doesn't seem to apply when in a virtual terminal/not in the Ubuntu (11.10) GUI. Not sure how to get at these settings from the terminal! Any help very much appreciated.

Background:
I'm running a program on my GPU using PyCUDA on Ubuntu 11.10. For my GPU to be useable, I have to go into a virtual terminal and stop X before running the PyCUDA stuff. Problems arise when the terminal thinks it has been inactive for a while (i.e. I have not typed anything), so stops sending stuff to my monitor. This interrupts the PyCUDA program and causes it to fail. I can sit at my computer and press keys every so often to prevent this, but the program takes quite a long time and I'd rather not sit in front of my computer all day...

---

### Post by ajaxdude on 2011-11-11
Trying to figure out the same thing over here.

I can press control+alt and F1-F6 and the screen slowly fades to black.
I can begin logging in before the screen goes completely black.

I can't find any info on this. I can see text plain as day, I don't think this is a driver issue, since I have it using ATI and NVIDIA cards across multiple versions of Ubuntu.

I'm honestly considering ditching ubuntu and going back to fedora.

---

### Post by torsionbar on 2011-11-11
Um, guys, it's called a screensaver.  And the answer to your question is the very first result when you Google for "linux console screensaver"  :rolleyes: 

The linked article below was written in 2006, but I've been using this same command since at least 1997, when I was running Slackware 3.1 and Redhat 4.2, so it certainly isn't anything new.  lol.

$ setterm -powersave off -blank 0

[http://www.cyberciti.biz/tips/linux-disable-screen-blanking-screen-going-blank.html](http://www.cyberciti.biz/tips/linux-disable-screen-blanking-screen-going-blank.html)

---

### Post by ManFromMars on 2011-11-14
Hahah, terminal n00b in total failure shocker. Didn't notice that my screen was still actually powered on - the blackness made me think it had shut down and I foolishly didn't check if the monitor power light was still on. I haven't used a screensaver for years. Thanks torsionbar :D

---

