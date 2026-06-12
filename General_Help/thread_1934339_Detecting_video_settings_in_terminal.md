---
title: "Detecting video settings in terminal"
date: 2012-03-02
forum: General Help
---

### Post by whatthefunk on 2012-03-02
I want to write a script that will toggle video settings.  I have two sets of settings saved using auto-disper/autorandr.  One set of settings is for single monitor mode and the other is for dual monitor mode.  I want my script to detect the current settings and then toggle to the other set of settings.  Ive got most of it laid out, but I cant figure out how to detect if my second monitor is active or not.  I know that is has something to do with the program nvidia-settings, but dont know which attribute to look at.  Any help??

OS: Kubuntu 11.10 with KDE 4.8
Graphics: Nvidia GeForce GTX 550 Ti

---

### Post by Khayyam on 2012-03-02
> **whatthefunk said:**
> I want to write a script that will toggle video settings.  I have two sets of settings saved using auto-disper/autorandr.  One set of settings is for single monitor mode and the other is for dual monitor mode.  I want my script to detect the current settings and then toggle to the other set of settings.  Ive got most of it laid out, but I cant figure out how to detect if my second monitor is active or not.  I know that is has something to do with the program nvidia-settings, but dont know which attribute to look at.  Any help?i

Whatever the card it'll be using/provding a 'framebuffer', so [fbset](http://linux.die.net/man/8/fbset) should provide information about the device and its current settings.

HTH ... khay

---

### Post by whatthefunk on 2012-03-02
Tried that....none of the options for fbset show whether my second monitor is activated or not.

---

### Post by whatthefunk on 2012-03-02
May have figured it out.
The outputs of disper -l -v from the auto-dipser script vary depending on which monitors are active.  As long as the variations are consistant, I can write a script to pick up on these differences.  Will play around and see if this works....

---

