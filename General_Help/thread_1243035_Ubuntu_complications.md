---
title: "Ubuntu complications"
date: 2009-08-17
forum: General Help
---

### Post by Sethun on 2009-08-17
So, I just switched from Windows XP home edition to Ubuntu version 9.04
I have a toshiba satellite A305-S6905 laptop, the installation went pretty smooth for the most part but my screen has been switching from fullscreen to a smaller resolution between restarts, also between restarts my cpu fan has been switching from full blast to low but at a constant rate of each. I figured it was just drivers and such, and if it is, help finding them would be great and if not just feedback is always helpful.

---

### Post by credobyte on 2009-08-17
*toshiba satellite A305-S6905* doesn't tell us what type of video card do you have.
Have you checked [COLOR=DarkGreen]System / Administration / Hardware drivers[/COLOR] ( only for proprietary drivers ) ?

---

### Post by Sethun on 2009-08-18
> **credobyte said:**
> *toshiba satellite A305-S6905* doesn't tell us what type of video card do you have.
Have you checked [COLOR=DarkGreen]System / Administration / Hardware drivers[/COLOR] ( only for proprietary drivers ) ?
I checked for proprietary drivers and there was none. I'm not sure what on board card I have I just know now that my 3D is working so my drivers are there, it's just switching to a different resolution for some odd reason.

---

### Post by lavinog on 2009-08-18
please post the output of
```

lshw -c video

```

If you have a ATI card that isn't supported by the proprietary driver, you are stuck with the open source driver.
By default the open source driver doesn't have DynamicClocks enabled which could be part of the issue with the fan.

---

### Post by Sethun on 2009-08-19
Oh thank you. I think I've got it working. :]

---

### Post by dvvdee on 2009-12-13
> **credobyte said:**
> *toshiba satellite A305-S6905* doesn't tell us what type of video card do you have.
Have you checked [COLOR=DarkGreen]System / Administration / Hardware drivers[/COLOR] ( only for proprietary drivers ) ?
*toshiba satellite A305-S6905 has intel *Mobile Intel Graphics Media Accelerator 4500MHD[I] graphic card. and the always working fan is may be cpu fan.
my laptop is working like above one's. is it ok? or not?
sorry for my poor english.
[/I]

---

### Post by lavinog on 2009-12-14
Usually there is one fan for both the cpu and the gpu.
The gpu could be working too hard, try turning off desktop effects.

---

