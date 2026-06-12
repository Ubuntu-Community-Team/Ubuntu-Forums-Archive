---
title: "skype sound disappear"
date: 2009-11-10
forum: General Help
---

### Post by g.a. on 2009-11-10
Hi,

My skype (2.0.0.72-0medibuntu4) is behaving very strangely.

It works for a while and then it stops playing audio, I can even see the video of my interlocutor but no sounds. In such a case, the skype.real thread take more than 100% (?!) of the resources.

I have to 

```
ps -e | grep skype.real

9688 ?        00:05:59 skype.real

sudo kill -9 9688
```

in order to close skype (killall alone does not work). When running again it "almost" work but I have to kill skype after one single call.

In attach please find the only sound configuration that worked for me.

Any idea is welcome.

Best,
g.

---

### Post by gradinaruvasile on 2009-11-10
Upgrade Skype to 2.1 beta (thats the latest version and its stable):

[http://www.skype.com/go/getskype-linux-beta-ubuntu-32](http://www.skype.com/go/getskype-linux-beta-ubuntu-32)

Dont worry about the intrepid name of the.deb, it is for intrepid and newer versions of ubuntu.

Also u might consider removing PulseAudio from your system. It is a source of problems since it was introduced in Ubuntu. Since u use Jaunty i would recommend it because that PulseAudio version is really buggy. I did the same and my sound problems are gone since.
It is done by:
In a terminal:

gstreamer-properties

and select alsa input/output. Quit.

then

sudo apt-get remove --purge pulseaudio

in a terminal. Then reboot.

---

### Post by johnh10000 on 2009-11-10
> **gradinaruvasile said:**
> 

Also u might consider removing PulseAudio from your system. It is a source of problems since it was introduced in Ubuntu. Since u use Jaunty i would recommend it because that PulseAudio version is really buggy. I did the same and my sound problems are gone since.
It is done by:
In a terminal:

gstreamer-properties

I'm having audio problems too.  Tried the above and it say device not supported!  Yikes, it was.
any ideas?

---

### Post by g.a. on 2009-11-10
gradinaruvasile: I installed the new version from the skype website and, without modifying anything, it is working. Now it is few hours without any trouble and several calls.

So now from gstreamer-properties I have ALSA everywhere but skype has PulseAudio everywhere and it is working (the popmenu of skype only has pulseaudio).

I need skype for a couple of days more, I will then try to purge pulseaudio and see what skype does.

Best,
g.

---

### Post by gradinaruvasile on 2009-11-10
> **g.a. said:**
> gradinaruvasile: I installed the new version from the skype website and, without modifying anything, it is working. Now it is few hours without any trouble and several calls.

So now from gstreamer-properties I have ALSA everywhere but skype has PulseAudio everywhere and it is working (the popmenu of skype only has pulseaudio).

I need skype for a couple of days more, I will then try to purge pulseaudio and see what skype does.

Best,
g.

Hm. If its working no need to remove pulseaudio. You could try disabling it to see if something improves... I dont mean only Skype, all other sound using apps.
Instructions on removing pulseaudio:

[http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/](http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/)

---

