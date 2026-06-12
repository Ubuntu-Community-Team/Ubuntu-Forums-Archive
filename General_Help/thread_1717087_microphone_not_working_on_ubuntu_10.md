---
title: "microphone not working on ubuntu 10"
date: 2011-03-29
forum: General Help
---

### Post by joelkhayad on 2011-03-29
the microphone does not work on my skype, i'm using ubuntu 10 maverick. help pls

---

### Post by PoHandle on 2011-03-29
You should provide more information regarding your system to get a more accurate response.  Are you on a desktop or laptop?  What sound card are you using and what type of microphone?  Have you tinkered with sound settings?

However, generally you can:
Try opening a terminal and use alsamixer to adjust your audio device settings.
```
alsamixer
```
Press F4 to change to your capture devices, then see whether there is a switch that will allow you to select which microphone to use.  Also be sure that your microphone is not muted.

---

### Post by joelkhayad on 2011-03-29
im sorry,

here are some details, my laptop is sony vpcs111fm, im trying to make the internal microphone work with skype.

any ideas??

thanks a lot

---

### Post by prshah on 2011-03-29
> **joelkhayad said:**
> here are some details, my laptop is sony vpcs111fm, im trying to make the internal microphone work with skype.


Click the volume control applet (near the date/time), and choose "Sound preferences"; open the "Hardware" tab and ensure that you have atleast one input device (may be combined as a singe input/output device). Then, click the "Input" tab, and "choose" the relevant input device. Unmute the input and adjust volume until the sound meter registers sound.

if you run into problem, please post back with screenshot of the Sound preferences window, Input tab.

---

### Post by joelkhayad on 2011-04-04
I tried but still not working other alternative pls

---

