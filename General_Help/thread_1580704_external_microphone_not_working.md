---
title: "external microphone not working?"
date: 2010-09-23
forum: General Help
---

### Post by PsychoElixir on 2010-09-23
I have an M-AUDIO studio microphone that i can't seem to get to work on my ubuntu...any ideas??

Thanks in advanced

---

### Post by Vigh on 2010-09-23
Is it XLR, TRS or USB? I have an external Ashton CMV100 Condenser microphone working perfectly on ubuntu. Just need to make sure you have a class compliant soundcard, (which means automatically detected by linux) that also has an XLR connection or 1/4inch TRS jack respectively. If its USB, its most likely not supported. Good-luck. If its condenser- make sure you have a DC voltage supply, either via the jack and turned on, or via a 9VDC battery. I use 48VDC for mine from the soundcard direct.

I am using a Novation XIO-SYNTH as soundcard which is class compliant. XLR and TRS inputs 96Khz resolution at 24-bits.

---

### Post by PsychoElixir on 2010-09-23
hmmm sounds like im going to have a hard time...its USB....would Ubuntu studio solve my problem?...is there literally no way Ubuntu will work?

---

### Post by Vigh on 2010-09-23
Whats the exact model of your microphone, I will look at the specs and see if there is a way to get it to work.

---

### Post by PsychoElixir on 2010-09-23
Honestly I'll tell you the truth im going crazy looking for the model to this damn microphone...all it says is "M-AUDIO Producer USB"...i've been looking through the booklets regarding the microphone and i cant find a model anywhere...i even popped it open..the card inside says "m-audio usb mic rev-A0"...doubt any of that helps

---

### Post by Vigh on 2010-09-23
Go to the M-Audio website, and look at the pictures, will be able to identify from that. Although I couldn't see any USB-only mics, they were all XLR.

---

### Post by PsychoElixir on 2010-09-23
[http://crunchgear.com/wp-content/uploads/imgp2232.JPG](http://crunchgear.com/wp-content/uploads/imgp2232.JPG)

^^thats a picture of it

[http://www.m-audio.com/products/en_us/ProToolsVocalStudio.html](http://www.m-audio.com/products/en_us/ProToolsVocalStudio.html)

^^website for it

---

### Post by Vigh on 2010-09-23
No luck mate. Its not operating system class-compliant (PLUG AND PLAY) and requires drivers to work on both Windows and Mac! And unfortunately they dont appear to write drivers for linux. So basically the M-audio usb producer mic is a no-go on linux/ubuntu. However any of the normal M-Audio or any other brand for that matter microphones with XLR jacks will work on linux, provided you have a supported ALSA soundcard with an XLR jack on it and phantom power supply. Sorry.

Basically what youve got is a soundcard/mic combo package. Unfortunately its not supported. Best setup, is to have a soundcard and a mic seperately rather than combo package. Then you can definately make sure its supported and use any XLR microphone.

Regards

Ant

---

### Post by PsychoElixir on 2010-09-23
Yea im running on an HP laptop...so i suppose that would answer my second question whether it would work ubuntu studio or not

---

### Post by Vigh on 2010-09-23
Nah won't work on studio either. At least I don't think so. Studio is basically exactly the same as normal ubuntu, but has the music/graphics software pre-installed and a low-latency audio kernel. If you want to have a linux audio production studio, you have to research and select your hardware/kit carefully, to make sure its supported. Its critical.

---

### Post by Vigh on 2010-09-23
My current setup is-

TOSHIBA Laptop
Novation XIO SOUNDCARD/MIDI-CONTROLLER and Synthesizer
Ashton CMV100 Supercardiod Condenser Mic
Ableton Live
Audacity

basically
+additional plugins
+free ubuntu music apps

---

