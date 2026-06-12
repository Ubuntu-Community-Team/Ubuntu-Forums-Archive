---
title: "Headphones and speakers play at same time"
date: 2011-05-24
forum: General Help
---

### Post by Jordy7 on 2011-05-24
(noob)I am running ubuntu 11.04 on my ASUS k60IJ, the sound plays out of both my earbuds and the internal speakers of the laptop. Any suggestions?

---

### Post by linuxinstalledfromhdd on 2011-05-24
I think this is natty issue.

---

### Post by lidex on 2011-05-24
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications-> Accessories-> Terminal"]

---

### Post by Jordy7 on 2011-05-25
Sorry I had to sleep, here is that link [http://www.alsa-project.org/db/?f=58f0ef88065b66aea0f1eabc73c8c50fd5f729e3](http://www.alsa-project.org/db/?f=58f0ef88065b66aea0f1eabc73c8c50fd5f729e3)

---

### Post by lidex on 2011-05-25
Have you tried switching the 'Connector' on output tab of 'Sound Preferences' to headphones?
If that doesn't help, try this:
```
echo "options snd-hda-intel model=auto" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

---

### Post by Jordy7 on 2011-05-25
Yeah I just tried that.

---

### Post by lithopsian on 2011-05-25
With ALSA being such a black art, most people are happy to get sound out of anything at all.  My recommendation is don't touch anything in case you break it :D

You should have individual volume control for each channel in the mixer.  Not as convenient as the headphones auto-muting but it is something.

If it's any consolation, my non-Natty non-laptop system does the same thing, but then I have built my own custom kernel and my sound settings are not at all standard.

---

