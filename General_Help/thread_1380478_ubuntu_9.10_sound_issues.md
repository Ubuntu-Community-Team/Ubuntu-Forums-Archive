---
title: "ubuntu 9.10 sound issues"
date: 2010-01-13
forum: General Help
---

### Post by wwsoft on 2010-01-13
Hello , I am using Ubuntu 9.10 one a Acer Aspire One laptop , for some reason the sound does not work 100% (& seems to work less with every update) of the time with the volume up. Are there any ways to fix this (or any other cases of this happening)?

---

### Post by mörgæs on 2010-01-14
9.10 uses Pulseaudio and 9.04 uses Alsa. 

How does your computer work with a 9.04 live CD (that is, Alsa)?

---

### Post by mikewhatever on 2010-01-14
> **wwsoft said:**
> Hello , I am using Ubuntu 9.10 one a Acer Aspire One laptop , for some reason the sound does not work 100% (& seems to work less with every update) of the time with the volume up. Are there any ways to fix this (or any other cases of this happening)?

Well, does the sound work 99%? 98? In short, what is the problem exactly?

> **mörgæs said:**
> 9.10 uses Pulseaudio and 9.04 uses Alsa. 

How does your computer work with a 9.04 live CD (that is, Alsa)?

Both 9.10 and 9.04 use pulseaudio by default, in fact, Ubuntu switched to PA since 8.04 in 2008.

---

### Post by mörgæs on 2010-01-14
> **mikewhatever said:**
> Both 9.10 and 9.04 use pulseaudio by default, in fact, Ubuntu switched to PA since 8.04 in 2008.

Oops, thanks for correcting.

---

### Post by akakingess on 2010-01-14
Also, do the headphones work at all, I have seen instances where the headphones worked for some reason and the speakers didn't?  I only ask because then we could look for that other thread and see what the solution there was.

---

### Post by wwsoft on 2010-01-14
> **akakingess said:**
> Also, do the headphones work at all, I have seen instances where the headphones worked for some reason and the speakers didn't?  I only ask because then we could look for that other thread and see what the solution there was.
  Actually I use headphones (I also have 2 other sets of speakers that I do test the lack of sound with)

[QUOTE=mikewhatever]Well, does the sound work 99%? 98? In short, what is the problem exactly?[/QUOTE]

the 30-40% of the time the sound does not work. I have no idea what causes it ...

---

### Post by mörgæs on 2010-01-15
> **wwsoft said:**
> 
the 30-40% of the time the sound does not work. I have no idea what causes it ...

-and neighter has the people in this forum, until they get a little more information :-) 

A first step could be to examine, wether there was a similar problem in 9.04, or it first appeared in 9.10.

---

### Post by wwsoft on 2010-01-15
> **mörgæs said:**
> -and neighter has the people in this forum, until they get a little more information :-) 

A first step could be to examine, wether there was a similar problem in 9.04, or it first appeared in 9.10.

8.04 desk: live failed to boot 
9.10 Netbook: live failed to boot
9.10 desk: nowere to be found

well ... it seems Im stuck with using ubuntu 9.10 ------.14 
because the sound works when I least expect it

---

### Post by mörgæs on 2010-01-16
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats](https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats)

You can burn CD's from here:
[http://releases.ubuntu.com/jaunty/](http://releases.ubuntu.com/jaunty/)
[http://releases.ubuntu.com/karmic/](http://releases.ubuntu.com/karmic/)

Is your machine set to boot from the CD?

---

### Post by wwsoft on 2010-01-16
> **mörgæs said:**
> [https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats](https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats)

You can burn CD's from here:
[http://releases.ubuntu.com/jaunty/](http://releases.ubuntu.com/jaunty/)
[http://releases.ubuntu.com/karmic/](http://releases.ubuntu.com/karmic/)

Is your machine set to boot from the CD?

the try Ubuntu without changes ...   on the disk comes up with an error is what I ment

---

### Post by running_rabbit07 on 2010-01-16
Maybe uninstalling Pulde Audio and installing Alsa will do the job. No sense burning LiveCDs just to try audio programs.

[http://ubuntuforums.org/showthread.php?t=1307019](http://ubuntuforums.org/showthread.php?t=1307019)

---

