---
title: "No sound in ubuntu"
date: 2010-10-17
forum: General Help
---

### Post by Sam3280 on 2010-10-17
Hi,
I have a new computer all is now working except for sound, Sound works on openSUSE but not Ubuntu 10.04 or 10.10, I have tried using two sets of speakers and used the suggestions listed here [https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems)

I am using the sound card in the motherboard GA-MA74GMT-S2 [http://www.gigabyte.com/products/product-page.aspx?pid=3582#ov](http://www.gigabyte.com/products/product-page.aspx?pid=3582#ov)

Can anybody suggest anything. I have tried all the option in sound settings, I am trying to set up 2.1 channel speakers

---

### Post by Hippytaff on 2010-10-17
whats the output of 

```

aplay -l

```l is a lowercase L not uppercase I :-)

---

### Post by Sam3280 on 2010-10-17
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC887 Analog [ALC887 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC887 Digital [ALC887 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by Hippytaff on 2010-10-17
[http://art.ubuntuforums.org/showthread.php?t=1468048](http://art.ubuntuforums.org/showthread.php?t=1468048)

this thread may be of some use - if you need more help keep posting :-)

---

### Post by Sam3280 on 2010-10-18
I installed the ALSA mixer but it wont open it loads and dissapears.
Any other ideas please

---

### Post by Hippytaff on 2010-10-18
> **Sam3280 said:**
> I installed the ALSA mixer but it wont open it loads and dissapears.
Any other ideas please
 
Can you get sound now (from an mp3 or cd)?
 
Do you get any error messages when you type alsamixer in the Terminal?

---

### Post by Sam3280 on 2010-10-19
when i try to launch alsa mixer from terminal it says 
cannot load mixer controls: Invalid argument

---

### Post by mylo9000 on 2010-10-21
i have to say that i too am being afflicted by this same issue, alsamixer reports the same error however my mobo is a GA-H55M-S2. the audio codec is ALC887 as reported by aplay -l,

on a side note i do get audio through my logitech usb headset. but the on-board sound is not working. i have submitted my errors to launchpad, though it seems the emails have stopped, so i guess there is no answer as of yet. Its a pity this new system of mine feels cheapened having to use windows on it thus far. Not having proper audio is proving to be a major set back for me.

i have tried installing the latest alsa driver but that just made the system hang on boot. do i hand to scrap that install.

if anyone has any insight to this issue, please let me know.

ty :)

---

### Post by Sam3280 on 2010-10-21
I bought a 2.1 channel logitech speaker system for the new computer and cant use them yet

---

### Post by Sam3280 on 2010-10-21
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/662059](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/662059) Here is my bug report if you want to submit that it affects you too

---

### Post by Sam3280 on 2010-10-23
SOLVED!!! thanks to members at launchpad

Solution:
In terminal type: sudo nano /etc/modprobe.d/alsa-base.conf

Add the following 2 lines at the end of the file, save and restart.

alias snd-card-0 snd-hda-intel
options snd-hda-intel model=auto

Solution thanks to gbhuvanesh and thanks to Jeff Clemmer for directing me to the solution

---

### Post by Hugoadelgado on 2010-10-25
I just installed Ubuntu Lucid into this computer, I have the same mother board, ( MA74GMT-S2) I m trying to use the on board  sound (Realtek ALC888B codec) and i can't get sound, i tried the solution on this tread and still no sound. Can someone please help me,, i really like UBUNTU and do not want to go back to Windows, but i can have a computer without sound.

---

### Post by satish_j on 2010-10-28
> **Sam3280 said:**
> SOLVED!!! thanks to members at launchpad

Solution:
In terminal type: sudo nano /etc/modprobe.d/alsa-base.conf

Add the following 2 lines at the end of the file, save and restart.

alias snd-card-0 snd-hda-intel
options snd-hda-intel model=auto

Solution thanks to gbhuvanesh and thanks to Jeff Clemmer for directing me to the solution

Thanks,that did the work for me as well.

---

