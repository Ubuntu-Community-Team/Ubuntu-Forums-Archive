---
title: "Sound does not work"
date: 2011-07-27
forum: General Help
---

### Post by windows4life on 2011-07-27
I've had sound problems for a very long time with Ubuntu. 

It once worked fine. Then it got distorted, but I used headfones so that solved that. But now it seems its completely disfunctional. 

The sound doesn't work at all. 

I've tried searching over the net for tutorials but they don't seem to work. So can anyone help me please?

Thanks in advance. :)

---

### Post by XubuRoxMySox on 2011-07-27
For me the problem (in Xubuntu) was PulseAudio. Replacing it with ALSA cured my sound problem. Here's how I did it in Xubuntu, so you'll have to adapt these instructions to Ubuntu:

Click on the **Menu**, select **Settings** &#8211;>**Session & Startup**, and click on the **Application Autostart** tab.

**Uncheck** &#8220;PulseAudio Sound System&#8221; and &#8220;Volume Control.&#8221;

Now to remove PulseAudio and install ALSA, open a Terminal and type:

```
sudo killall pulseaudio
sudo apt-get purge pulseaudio
sudo apt-get purge pulseaudio-utils gstreamer0.10-pulseaudio libpulse-browse0 paman pavumeter pavucontrol
sudo rm -rf /etc/asound.conf
sudo rm ~/.pulse-cookie
```

You will be asked for your password, since you are acting as Root (&#8220;Administrator,&#8221; if you wish). Now to install ALSA:

With the Terminal still open, type:

```
sudo apt-get install -y libalsaplayer0 esound
```

Now you can right-click your **Panel**, select **Add to Panel**, and choose &#8220;Volume Control.&#8221; 

Again, that's for Xubuntu (10.04), so you'll need to adapt these instructions for Ubuntu.

Hoping this helps,
Robin

---

### Post by lkjoel on 2011-07-27
Try Sound Troubleshooting in my signature.

---

### Post by Kira_Belka on 2011-07-27
Hi .. lspci plz first)

---

### Post by windows4life on 2011-07-28
> **dixiedancer said:**
> For me the problem (in Xubuntu) was PulseAudio. Replacing it with ALSA cured my sound problem. Here's how I did it in Xubuntu, so you'll have to adapt these instructions to Ubuntu:

Click on the **Menu**, select **Settings** –>**Session & Startup**, and click on the **Application Autostart** tab.

**Uncheck** “PulseAudio Sound System” and “Volume Control.”

Now to remove PulseAudio and install ALSA, open a Terminal and type:

```
sudo killall pulseaudio
sudo apt-get purge pulseaudio
sudo apt-get purge pulseaudio-utils gstreamer0.10-pulseaudio libpulse-browse0 paman pavumeter pavucontrol
sudo rm -rf /etc/asound.conf
sudo rm ~/.pulse-cookie
```You will be asked for your password, since you are acting as Root (“Administrator,” if you wish). Now to install ALSA:

With the Terminal still open, type:

```
sudo apt-get install -y libalsaplayer0 esound
```Now you can right-click your **Panel**, select **Add to Panel**, and choose “Volume Control.” 


Sorry, I'm a n00b so I don't know how to adapt to my Ubuntu. I lost you at the first step. There's no 'menu' or 'session & startup' that I can seem to locate. 

I did however open the terminam and can't get past the second stage, I get this error:

> E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

---

### Post by XubuRoxMySox on 2011-07-28
> **windows4life said:**
> Sorry, I'm a n00b so I don't know how to adapt [your Xubuntu instructions] to my Ubuntu. 

Give it a little while... I'm sure an Ubuntu user that knows how to do it in Ubuntu will be along to adapt" those instructions to Ubu instead of Xubu.

But Kira's advice is best, before you proceed any further:

Open a terminal and type
 ```
lspci
```

Then post the output here. That will help us help you better!

---

