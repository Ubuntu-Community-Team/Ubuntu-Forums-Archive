---
title: "No sound, everything slow..."
date: 2010-03-24
forum: General Help
---

### Post by pinenut on 2010-03-24
The problem started like this. 

In order to have Skype work better, I removed pulseaudio and installed Alsa. Everything went all right to this point. The Genome Alsa mixer worked ok too. 

Then I opened Skype and tried to set the audio and video options.
I have no mike input, so I set the option to the USB something option (my webcam is Logitech Quickcam Fusion) and I was able to record my voice. The speaker worked well. 

I found the video not working. I tried to test video by clicking 'TEST VIDEO' causing everything to freeze. I stopped X-server by issuing a key stroke of CTL-ALT-F2. The desktop died and I got an error message: serial8250: too much work for irq 16. I then logged on to CLI mode and removed Skype.

I rebooted and found there was no sound. I could open Genome-Alsa-Mixer, but I could not change anything. I can't even open Firefox because everything is so slow. 

Do I need to remove and re-install ALSA? How? I installed quite a few things for it. :confused:

---

### Post by byStanderone on 2010-03-24
...please try a sudo apt-get autoclean and do post a feedback

---

### Post by pinenut on 2010-03-24
> **byStanderone said:**
> ...please try a sudo apt-get autoclean and do post a feedback

Thank you for your prompt help. 
I did the following and it went OK. By the way, I had to do this after killing X-server because I can't type anything in Gnome terminal. 
```
$ suddo apt-get autoclean
```After rebooting, I don't see much has changed. :(
I am typing this from another computer because Ubuntu Karmic is not usable.

Edit:
Since no more help was forthcoming, I decided to try something on my own. It occurred to me that I experienced a similar problem when I did not set the driver for my nVidia graphic card. Although I had not done anything with the driver or GDM, I figured that the nvidia settings somehow got messed up. 

I rebooted it up in the recovery mode and dropped down to the root prompt.

> # cd /etc/X11
# cp xorg.conf.original xorg.conf
# reboot

After another reboot session, I reset nvidia-setting.
All my trouble got wipe out.

---

### Post by byStanderone on 2010-03-24
...well, nice to hear that!

---

