---
title: "Should I install ALSA? I don't know if I have ALSA or not."
date: 2010-01-27
forum: General Help
---

### Post by MKVCrazy on 2010-01-27
I can hear when I watch YouTube videos using **ALSA**, it shows in my **Sound Preference** (icon from system tray) when I am watching videos on Firefox. But somehow I get choppy and distorted output when I select **ALSA Audio Driver** in **VirtualBox** so I did a lot of searches and there's something I don't understand 100% but gives me the feeling that it'll fix it if I follow the instructions.
This page: [http://www.pulseaudio.org/wiki/PerfectSetup](http://www.pulseaudio.org/wiki/PerfectSetup)
Scroll down to where it says "**ALSA Applications**"

From my understanding, that plugin is going to make ALSA outputs to PulseAudio server and **PulseAudio** will output the sound for me which is what I want because when I select **PulseAudio** in **VirtualBox**, I get clear audio output but since there's something wrong with it capturing audio in **VirtualBox**, I can't use it for IM or Rosetta Stone.

So I went on with trying to make **PulseAudio** defaults and then I did a quick check whether I have alsalib or not in my **Synaptic Package Manager**. I am guessing I don't have that. Right? See the screenshot in attachment please.

From my understanding here, I don't have the followings:
***alsalibs*** (this is required to install alsaplugins)
***alsaplugins*** (this is required to make the **PulseAudio** default)

So since, I don't have the above to I am planning to install the latest ones from these pages:
**ALSA Plugins 1.0.22**
[ftp://ftp.alsa-project.org/pub/plugins/](ftp://ftp.alsa-project.org/pub/plugins/)
&
** ALSA Libs 1.0.22**
[ftp://ftp.alsa-project.org/pub/lib/](ftp://ftp.alsa-project.org/pub/lib/)

So am I right about that I don't have the above two and need to install them?

I am willing to search my way out installing the above two but before I move on, I would like to know what I am doing is correct since there are kernel related stuff and I don't want to lose my currently working audio on my host OS. So please examine my situation for me. I'll really appreciate it.

---

### Post by MKVCrazy on 2010-01-28
Anyone, please?

---

