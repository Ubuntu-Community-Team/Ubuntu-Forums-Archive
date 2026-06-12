---
title: "My Toughbook Touchscreen is gone in Lucid"
date: 2010-09-24
forum: General Help
---

### Post by jeebustrain on 2010-09-24
I have a Toughbook CF-74 with a "Fujitsu USB Touch Panel" (how lsusb used to enumerate it). It used to work fairly well up until Karmic (couldn't get the calibration perfect around the edges), but it's just not there anymore in 10.04. I can only assume it's a kernel thing, because I tried some test installs of Debian Testing and OpenSUSE 11.3 (both with newer kernels than Lucid) and it's not there either. 

I've searched around here and around the net and can't find much help. I tried to manually load a kernel module for a different Fujitsu touch screen (from an actual Fujitsu laptop), but it didn't seem to detect anything.

There's not a whole lot of info out there about running Linux on a CF-74, so I think I'm in kind of in uncharted territory with some of this stuff.

---

### Post by jeebustrain on 2010-09-28
well - I figured out my problem (at least I'm pretty sure). I think my touchscreen is just dead. It was acting up a few months back before I upgraded it and I just attributed it to something screwy in my xorg config. I just loaded up a Karmic live CD and installed xserver-xorg-input-evtouch and tried to run the calibration tool and it doesn't even pick up any input. 

I did some reading in the Toughbook forum on notebookreview.com and apparently the touchscreen just dying is not an uncommon occurance. 

Well fiddlesticks... At least the rest of the laptop works. Not bad for being almost 4.5 years old.

---

