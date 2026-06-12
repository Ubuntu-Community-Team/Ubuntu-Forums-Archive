---
title: "I need some help, have alot of questions!"
date: 2012-05-19
forum: General Help
---

### Post by stepking2 on 2012-05-19
Let's start!

I have a game on my laptop called Stepmania(version 3.9a), and when I restart my laptop, the game works great and no lag, but if I go in and out of the game a couple of times it doesn't run any more. And when I look at the log file, this is what it says:

00:00.007: StepMania 3.9 
00:00.007: Log starting 2012-05-19 14:22:59 
00:00.007:   
00:00.007: Reading 'Data/Defaults.ini' failed: No such file or directory 
00:00.008: Reading 'Data/Static.ini' failed: No such file or directory 
00:00.099: Loading window: gtk 
00:00.099: OS: Linux ver 030200 
00:00.099: Crash backtrace component: x86 custom backtrace 
00:00.099: Crash lookup component: dladdr 
00:00.099: Crash demangle component: cxa_demangle 
00:00.099: Runtime library: glibc 2.15 
00:00.099: Threads library: NPTL 2.15 
00:00.099: TLS is available 
00:00.099: AnnouncerManager::AnnouncerManager() 
00:00.099: Reading 'Data/Static.ini' failed: No such file or directory 
00:00.099: ThemeManager::SwitchThemeAndLanguage: "default", "" 
00:00.119: Initializing driver: ALSA 
///////////////////////////////////////// 
00:00.120: WARNING: Got file 'kcore' in 'proc/' from list, but can't stat? (Value too large for defined data type) 
///////////////////////////////////////// 
///////////////////////////////////////// 
00:00.126: WARNING: Got file 'kcore' in 'proc' from list, but can't stat? (Value too large for defined data type) 
///////////////////////////////////////// 
00:00.127: ALSA: Advanced Linux Sound Architecture Driver Version 1.0.24. 
00:00.127: ALSA Driver: 0: HDA ATI SB [SB], device 0: ALC272X Analog [ALC272X Analog], 0/1 subdevices avail 
00:00.128: ALSA Driver: 1: HD-Audio Generic [Generic], device 3: HDMI 0 [HDMI 0], 1/1 subdevices avail 
00:00.128: ALSA error: pcm_hw.c:1293 snd_pcm_hw_open: open '/dev/snd/pcmC0D0p' failed (-16) (Device or resource busy) 
00:00.129: Couldn't load driver ALSA: dsnd_pcm_open(hw:0): Device or resource busy 
00:00.129: Initializing driver: ALSA-sw 
00:00.129: OS: Linux ver 030200 
00:00.129: ALSA error: pcm_hw.c:1293 snd_pcm_hw_open: open '/dev/snd/pcmC0D0p' failed (-16) (Device or resource busy) 
00:00.129: Mixing 0.000000 ahead in 0 Mix() calls 
00:00.129: Couldn't load driver ALSA-sw: dsnd_pcm_open(hw:0): Device or resource busy 
00:00.129: Initializing driver: OSS 
00:00.129: Mixing 0.000000 ahead in 0 Mix() calls 
00:00.129: Couldn't load driver OSS: RageSound_OSS: Couldn't open /dev/dsp: No such file or directory 
00:00.129:  
00:00.129: ////////////////////////////////////////////////////// 
00:00.129: Exception: Couldn't find a sound driver that works 
00:00.129: ////////////////////////////////////////////////////// 
00:00.129:  
00:00.129: Language: english 
00:00.129: Theme: default

I have some icons in Dash Home, which is icons from Wine installations/uninstallations, how do I remove them?

Sometimes when I shutdown my laptop, it gets stuck in either, the Ubuntu boot screen or a mix between graphics, boot screen and wallpaper. How can I fix that?

I want to change the color theme, but everytime I do, it switches right back to the color of my wallpaper, how can I fix that?

And is there and guide or video where I can learn more about Ubuntu, the features of it, troubleshooting and how it works?

Thanks in advance for help :-D

---

### Post by 2F4U on 2012-05-19
If you are looking for a guide on Ubuntu, why not start with the official documentation:

[https://help.ubuntu.com/](https://help.ubuntu.com/)

---

### Post by MG&amp;TL on 2012-05-19
> **stepking2 said:**
> 

I have some icons in Dash Home, which is icons from Wine installations/uninstallations, how do I remove them?

Sometimes when I shutdown my laptop, it gets stuck in either, the Ubuntu boot screen or a mix between graphics, boot screen and wallpaper. How can I fix that?

I want to change the color theme, but everytime I do, it switches right back to the color of my wallpaper, how can I fix that?

And is there and guide or video where I can learn more about Ubuntu, the features of it, troubleshooting and how it works?

Thanks in advance for help :-D


Wine-I *think* you should be able to find said icons in /usr/share/applications (I'm not sure-it's wine),which you then should be able to delete.

...colour theme? You mean the launcher/dash colour scheme? Well, last time I tried, MyUnity worked for that. Although changing your wallpaper will probably override that. (the wallpaper colour is a new feature,  it's still a little...fragile)

---

### Post by Erik1984 on 2012-05-19
I think it's better to start separate threads for these issues. Regarding your first question, it could be that the sound system is still 'occupied' from a previous run of the game. It could help to kill PulseAudio (PulseAudio will restart automatically).

```
pkill pulseaudio
```

---

### Post by stepking2 on 2012-05-19
I couldn't find the icons in the folder, that MG&TL mentioned.

On the issue with Stepmania, the game worked after I went into an emulator and out.
But I will hold on to the command, that Euroman mentioned.

I have MyUnity, but there wasn't any option to fix that.

But do any of you have an answer to my question regarding the shutdown of my laptop? Or is that something I have to get used to? :-)

---

