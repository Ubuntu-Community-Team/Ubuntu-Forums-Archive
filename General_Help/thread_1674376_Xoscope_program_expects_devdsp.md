---
title: "Xoscope program expects /dev/dsp"
date: 2011-01-23
forum: General Help
---

### Post by arvevans on 2011-01-23
I downloaded and installed "xoscope" from the Ubuntu repository but found that it is hard-coded to use /dev/dsp for access to the sound card.  Ubunto 10.10 does not have /dev/dsp available for use by this legacy application.

Is there some sort of work-around for legacy applications which expect /dev/dsp to be available as a sound card interface?

---

### Post by arvevans on 2011-01-26
bump

---

### Post by arvevans on 2011-01-26
bump

---

### Post by arvevans on 2011-01-29
bump

---

### Post by arvevans on 2011-01-29
Since there are a number of legacy applications in the Ubuntu repository which rely on /dev/dsp or /dev/snd for their operation, it might be nice if there were a way to cull these now defective programs by doing a source code search for "/dev/dsp" and/or "/dev/snd".

An alternative might be for someone to write a shim program that could reside at /dev/dsp and /dev/snd and provide the proper interface to newer sound card interfaces.  This could then preserve the utility of those old and fairly popular legacy applications.

---

### Post by Tristan Chambers on 2011-02-04
I had the same problem with xoscope. Highly annoying! But there is a package in the ubuntu repository that provides a work around for OSS dependent applications called alsa-oss.

sudo apt-get install alsa-oss
then type:
aoss xoscope

aoss loads xoscope and somehow tricks it to think it's using OSS.

References:
[https://help.ubuntu.com/community/SoundTroubleshooting#Getting%20more%20than%20one%20application%20to%20use%20the%20soundcard%20at%20the%20same%20time](https://help.ubuntu.com/community/SoundTroubleshooting#Getting%20more%20than%20one%20application%20to%20use%20the%20soundcard%20at%20the%20same%20time)

---

### Post by Tristan Chambers on 2011-02-04
To address your idea about a systematic shim to resolve this issue: We could at least have the package alsa-oss be a dependency of xoscope. And maybe we could modify the ubuntu package such that the executable 'xoscope' is actually a script that calls "aoss xoscope." I don't know if this is kosher in the package maintenance world, but I thought it might get the conversation started.

---

### Post by kf7nnz on 2011-02-05
Would it be possible to simply create a /dev/dsp and symbolically link it to the correct device, in my case, /dev/snd/controlC0?

---

### Post by Tristan Chambers on 2011-02-07
I tried that and it didn't work. Linking to the alsa device files in /dev/snd/ isn't sufficient, I think because emulation is required. That's my guess at least.

---

### Post by nikos.theos on 2011-02-14
I tried "padsp" & "aoss" commands with no success in Maverick. I installed package "oss-compat" (OSS kernel modules seems to still be blacklisted), but I saw no progress...
Xoscope can use Esound server for it's input. Ubuntu's default sound server -Pulseaudio- is compatible with Esound (can act as a replacement), but the xoscope's binary version is not compiled with Esound support. So I compiled xoscope again (with Esound support of course):

>sudo apt-get install build-essential fakeroot libesd0-dev
>sudo apt-get build-dep xoscope
>mkdir btmp; cd btmp
>apt-get source xoscope
>cd xoscope-2.0/
>dpkg-buildpackage -b
>cd ..; rm -rf xoscope-2.0/
>sudo dpkg -i xoscope_2.0-3.1_amd64.deb     # instead of amd64, i386 ?

Then install some useful utilities for pulseaudio:
>sudo apt-get install padevchooser
[Alt + F2] : pavucontrol
Go to "output devices" and select Line-In (or Mic) and tick it as default.
Now mute your speakers and execute:
>parec | paplay --raw

Open xoscope and see a waveform of your line-in signals (no DC offset).
When you finish press [Ctl + C] to the terminal, to stop input playback.
Be careful and keep input voltage below 2-1 Volts!

Does anybody know how to connect line-in with pulseaudio's xoscope client, with pulse's commands, to avoid playback to speakers?

---

### Post by seventeener on 2011-05-13
Thank you nikos.theos, your instructions did the trick for me! Now I can run pavucontrol->recording and choose the input device for xoscope. It works! I don't run parec as you suggested. 
There is a minor problem that whenever I change any setting in xoscope, the input device in pavucontrol resets back to "Monitor of internal audio analog stereo". I don't see how to set a device as default.

---

### Post by nikos.theos on 2011-05-15
Unfortunately I have to use parec...
Seventeener check the screenshot (step number 3 to set the default device). 

[IMG]http://img197.imageshack.us/img197/1452/pavucontrol.png[/IMG]

It may solve your problem.

---

### Post by linuxonbute on 2011-09-18
> **Tristan Chambers said:**
> I had the same problem with xoscope. Highly annoying! But there is a package in the ubuntu repository that provides a work around for OSS dependent applications called alsa-oss.

sudo apt-get install alsa-oss
then type:
aoss xoscope

aoss loads xoscope and somehow tricks it to think it's using OSS.

References:
[https://help.ubuntu.com/community/SoundTroubleshooting#Getting%20more%20than%20one%20application%20to%20use%20the%20soundcard%20at%20the%20same%20time](https://help.ubuntu.com/community/SoundTroubleshooting#Getting%20more%20than%20one%20application%20to%20use%20the%20soundcard%20at%20the%20same%20time)

Just to say this worked for me running Ubuntu 10.10  kernel 2.6.35-30-generic #56-Ubuntu SMP

---

### Post by soreau on 2011-11-14
I found this worked for me on 11.04:

```
padsp xoscope
```

---

### Post by gerard on 2012-02-21
> **Tristan Chambers said:**
> I had the same problem with xoscope. Highly annoying! But there is a package in the ubuntu repository that provides a work around for OSS dependent applications called alsa-oss.

sudo apt-get install alsa-oss
then type:
aoss xoscope

aoss loads xoscope and somehow tricks it to think it's using OSS.

References:
[https://help.ubuntu.com/community/SoundTroubleshooting#Getting%20more%20than%20one%20application%20to%20use%20the%20soundcard%20at%20the%20same%20time](https://help.ubuntu.com/community/SoundTroubleshooting#Getting%20more%20than%20one%20application%20to%20use%20the%20soundcard%20at%20the%20same%20time)

I simply changed the commandline in the Systems/Preferences/MainMenu
And it works.

---

