---
title: "Troubles starting the desktop (stuck at the commandline)"
date: 2011-06-23
forum: General Help
---

### Post by n0c0d3 on 2011-06-23
Hi,

I recently changed the nvidia-driver (I could choose from 3: 'current', '137' and '78' or something like that), because I wanted to see if the others had better resolution options, but I don't remember which  used. I think it was 'current' and wanted to try '137' (or whatever the number may be). After I rebooted I only got the command-line. I've had problems like this before, but normally, after some fooling around with commands I got from questions I asked before and web-searches, I'm usually able to get the GUI going again. Not this time. I'm stuck.

I'm using Xubuntu 10.04. 'startxfce4' only results in an error.

I've tried to download and re-install the 'nvidia-current' driver, but to no avail.


Anyone who can help me get to the GUI again?

Thanks in advance,
Bart

---

### Post by TeoBigusGeekus on 2011-06-23
Delete your xorg file
```
sudo rm /etc/X11/xorg.conf
```
and try again.

---

### Post by n0c0d3 on 2011-06-23
Thanks TeoBigusGeekus, that was really easy and it even worked. Things can be so simple when you know what to do...

I'm still trying to figure out if it's possible how to get a higher screen resolution, eg. 1280x1024 (now it's 1024x760), but there's no higher resolution in the options. I'll be looking around for an answer, but if someone has a simple solution I'd be grateful.

Thanks!
Bart

---

### Post by TeoBigusGeekus on 2011-06-23
How do you try to set the resolution?

---

### Post by n0c0d3 on 2011-06-23
From the settings-manager/Display screen. I was using the 'nvidia-current' driver (on xubuntu), but just tried to switch to version 173 (correction from the above number I erroneous stated). But the max resolution on this one is even worse: 640x480. So I've just gone back to 'nvidia-current' and after rebooting I have to delete the xorg.conf file again.
In the hardware nvidia xserver settings screen I tried to find out if there are options to change to other resolutions but then I get the error "You do not seem to be using the NVIDIA X driver. Please edit the X configuration file (just run 'nvidia-xconfig' as root) and restart the X-server".
When I do that I get :

WARNING: Unable to locate/open the X configuration file.
sh: pkg-config not found
New X configuration file written to '/etc/X11/xorg.conf'.

So then I reboot again, and I get stuck at the command-line again and I have to delete the xorg.conf file again, reboot again to get in the GUI.

So I'm getting the run-around, but no way to option change to a higher resolution.

Maybe some backgrund info is helpful. I used to have a better resolution, but I changed to a monitor-switch so I can use 1 monitor for 2 computers. On the other computer (WinXP) this gives no problem and I can use 1280x1024, but maybe Ubuntu doesn't recognize the monitor this way?

---

### Post by TeoBigusGeekus on 2011-06-23
```
gksu nvidia-settings
```
Do all your configuration from there - after you're done, don't forget to press the "Save to X configuration file" button.

---

### Post by n0c0d3 on 2011-06-23
That's the same as what I meant with the "nvidia xserver settings screen". That's when I get the error-message that politely tells me: "You do not seem to be using the NVIDIA X driver. Please edit the X  configuration file (just run 'nvidia-xconfig' as root) and restart the  X-server".

---

### Post by wildmanne39 on 2011-06-23
> **n0c0d3 said:**
> That's the same as what I meant with the "nvidia xserver settings screen". That's when I get the error-message that politely tells me: "You do not seem to be using the NVIDIA X driver. Please edit the X  configuration file (just run 'nvidia-xconfig' as root) and restart the  X-server".Hi, the current driver did not work for me, I have to use the 173, but it works great, I had to manually set my resolution in xorg.conf, I will give you a link with instructions.
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

---

### Post by n0c0d3 on 2011-06-25
It looks I'm pretty much lost now. I changed to version 173 and there was a very basic xorg.conf file to which I added this line to the 'screens' section:
```
Modes         "1280x1024"  "1024x768"   "640x480"
```
Then I rebooted, but the computer goes in some sort of loop right after the Xubuntu splash-screen.
Then I had to boot in recovery-mode but there also the minimal graphics mode doesn't work and have to use the command line. I deleted the xorg.conf file, but to to no avail.

Then I tried to go back to 'nvidia-current' again:
```
apt-get install nvidia-current
```
but to no avail and I'm lost on the command-line again from here.

Any suggestions?

---

