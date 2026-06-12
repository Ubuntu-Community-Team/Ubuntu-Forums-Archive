---
title: "Game Crashes - Ubuntu 10.04"
date: 2010-07-10
forum: General Help
---

### Post by fmpjohnny on 2010-07-10
H-h-helppp, I am VERY new to Ubuntu, and in Linux in general..

I just dled the Stepmania-3.9.tar.gz from the site, and I extracted it to my desktop, tried running it, and I get nothing, it does not start up or even give me the error unless I check through terminal 
cd home/username/desktop/Stepmania-3.9

then ./stepmania

this is what it gives me

00:00.249: StepMania 3.9
00:00.249: Log starting 2010-07-10 03:48:36
00:00.249: 
00:00.249: Reading 'Data/Defaults.ini' failed: No such file or directory
00:00.249: Reading 'Data/StepMania.ini' failed: No such file or directory
00:00.249: Reading 'Data/Static.ini' failed: No such file or directory
00:00.362: Loading window: gtk
00:00.362: OS: Linux ver 020632
00:00.362: Crash backtrace component: x86 custom backtrace
00:00.362: Crash lookup component: dladdr
00:00.363: Crash demangle component: cxa_demangle
00:00.363: Runtime library: glibc 2.11.1
00:00.363: Threads library: NPTL 2.11.1
00:00.363: TLS is available
00:00.363: AnnouncerManager::AnnouncerManager()
00:00.363: Reading 'Data/GamePrefs.ini' failed: No such file or directory
00:00.363: Reading 'Data/Static.ini' failed: No such file or directory
00:00.419: ThemeManager::SwitchThemeAndLanguage: "default", ""
00:00.458: Initializing driver: ALSA
00:00.545: ALSA: Advanced Linux Sound Architecture Driver Version 1.0.21.
00:00.546: ALSA Driver: 0: HDA ATI HDMI [HDMI], device 3: ATI HDMI [ATI HDMI], 1/1 subdevices avail
00:00.546: ALSA Driver: 1: VIA 8237 [V8237], device 0: VIA 8237 [VIA 8237], 4/4 subdevices avail
00:00.546: ALSA Driver: 1: VIA 8237 [V8237], device 1: VIA 8237 [VIA 8237], 1/1 subdevices avail
00:00.546: ALSA error: pcm_hw.c:1293 snd_pcm_hw_open: open /dev/snd/pcmC0D0p failed (No such file or directory)
00:00.682: Couldn't load driver ALSA: dsnd_pcm_open(hw:0): No such file or directory
00:00.682: Initializing driver: ALSA-sw
00:00.682: OS: Linux ver 020632
00:00.683: ALSA error: pcm_hw.c:1293 snd_pcm_hw_open: open /dev/snd/pcmC0D0p failed (No such file or directory)
00:00.683: Mixing 0.000000 ahead in 0 Mix() calls
00:00.683: Couldn't load driver ALSA-sw: dsnd_pcm_open(hw:0): No such file or directory
00:00.683: Initializing driver: OSS
00:00.683: Mixing 0.000000 ahead in 0 Mix() calls
00:00.683: Couldn't load driver OSS: RageSound_OSS: Couldn't open /dev/dsp: No such file or directory
00:00.683: 
00:00.683: //////////////////////////////////////////////////////
00:00.683: Exception: Couldn't find a sound driver that works
00:00.683: //////////////////////////////////////////////////////
00:00.683: 
00:00.683: Language: english
00:00.683: Theme: default

This is also in the log.txt

So I am wondering what is up with all these errors, I'm missing .ini files, even though I JUST dled the tar.gz...
and the sound driver? Everything sound-wise has been fine.. Even playing SM3.9 in wine.

Can anyone enlighten me on what I am doing so wrong to play SM natively?

BTW.. My audio card is onboard, but I do have an HDMI audio out on my ati card. I am wanting to use the onboard.

Thank you so much for your support -bows-

Binary Source:
[http://www.stepmania.com/download.php?file=downloads/StepMania-3.9a-linux.tar.gz](http://www.stepmania.com/download.php?file=downloads/StepMania-3.9a-linux.tar.gz)

---

