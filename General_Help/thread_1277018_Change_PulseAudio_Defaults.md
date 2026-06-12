---
title: "Change PulseAudio Defaults?"
date: 2009-09-27
forum: General Help
---

### Post by TarasIv on 2009-09-27
When using Skype, I have to use to PulseAudio for my microphone and speakers. Well, the speakers work fine, but the microphone defaults to the speakers instead of my mic. I installed PulseAudio Manager, but when I choose the Microphone menu, the only options are Default and Other, and when you open other it says "Please enter source name:"
Is there anyway I can get PulseAudio to use my microphone.
Oh, and I am sure that my computer detects my mic and PulseAudio detects my mic because I can see it when I click on the PulseAudio Manager. Any help is greatly appreciated and thanks in advance!
Actually, a better way to put it would be, how can change the devices used on my PulseAudio server?

---

### Post by TarasIv on 2009-09-28
*bump*

---

### Post by TarasIv on 2009-09-28
*bump again*

---

### Post by TarasIv on 2009-09-28
*bump once more*

---

### Post by TarasIv on 2009-09-28
Nevermind, I figured it out myself. :)

---

### Post by can2002 on 2009-10-01
Hi there,

Any chance of telling us what you did to fix it???

Can

---

### Post by mpetrovsky on 2009-10-20
Hi,

I had the same issue. After running the "PusleAudio Device Chooser" (padevchooser), I had to change the "Default Source" to other and type in the source name. This was the painful part, I had to launch the "PulseAudio Manager", click on the Devices tab to find out the 1000 character source name. For me it was "alsa_input.usb_device_46d_990_C6D2D50C_if2_sound_card_0_alsa_capture_0".

It would have been nice to just have a dropdown :(

Hope this helps

---

### Post by jefkin on 2009-10-27
Wow, I hope I can get the same results, I tried, what mpetrovsky described (of course with a different 100 character device name.  And well it didn't work out of the box, going to try a reboot, to see if that helps matters.

---

### Post by jefkin on 2009-10-28
Unfortunately I was unable to get those results, and this was after 30 hours and 4 programmers have tried every crazy combination to get skype working with 9.04, finally a marketing guy needed me on skype, searched and found this:

[http://www.ustream.tv/recorded/2076737](http://www.ustream.tv/recorded/2076737)

This short video explains how to download the skype from skype.com, and then to install skype-static-oss, which you can do command line or from your favorite package manager.

I used my Synaptic and got it to run right away... easy.

Hope this helps someone!

---

