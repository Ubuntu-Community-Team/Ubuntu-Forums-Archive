---
title: "OSS4 and no sound from Firefox"
date: 2009-07-30
forum: General Help
---

### Post by razorboy5 on 2009-07-30
Hi
I installed OSS4 instead of Alsa and enjoying playing music on it
however i just installed Flash Player and trying to watch some vids online but can't hear any audio

looked in firefox preferences but nothing to change it to play from OSS4

any help?

thx

---

### Post by rajeevcelos on 2009-07-31
I also want to switch from ALSA to OSS4. Please tell me how to switch???

Thank You

---

### Post by Arup on 2009-07-31
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

If you follow the prodecedure in this link, it works like a charm with no issues. OSS4 is far superior in terms of sound and quality of recording compared to even the latest ALSA 1.20 as I have tested personaly. You will also find instructions on how to revert back to ALSA.

---

### Post by martinbaselier on 2009-07-31
If you enter the command below, the output should look like this.
```
ls /usr/lib/libflashsupport.so -al
lrwxrwxrwx 1 root root 38 2009-07-22 00:05 /usr/lib/libflashsupport.so -> /usr/lib/oss/lib/libflashsupport_32.so

```

Is it the same on your machine?

---

### Post by razorboy5 on 2009-07-31
[http://www.4front-tech.com/forum/viewtopic.php?t=3256](http://www.4front-tech.com/forum/viewtopic.php?t=3256)

thx to cesium solved it :D

---

### Post by SeijiSensei on 2010-05-18
(Kubuntu 9.10; Firefox 3.5.9; Shockwave Flash 10.0 r45 for 64-bit Linux)

Though this is an older thread, I've encountered the same problems trying to use OSS4 and the developmental version of the [64-bit Flash player for Linux]("http://labs.adobe.com/downloads/flashplayer10_64bit.html").  The solution is pretty simple, though it's been a bit hard to find through searching the web.

When I was using ALSA, Flash videos played fine along with everything else on the system, but after switching to OSS4 Flash audio stopped.  Regular applications like smplayer had no trouble using OSS4 if I specified that as the sound system in my configuration.  Unfortunately it appears that Adobe's binary for 64-bit Flash expects to find ALSA installed.

So I looked around to see if there was a simple way to emulate ALSA using OSS4 and found the answer [here]("http://www.4front-tech.com/wiki/index.php/Tips_And_Tricks#ALSA_Emulation").  In short, make sure you have the libasound2-plugins package installed, then create a file called .asoundrc in your home directory that looks like this:

~/.asoundrc
```
 pcm.!default
 {
   type oss
   device /dev/dsp
 }
 mixer.!default
 {
   type oss
   device /dev/dsp
 }
```

As soon as I did this, my Flash audio problems vanished.

---

