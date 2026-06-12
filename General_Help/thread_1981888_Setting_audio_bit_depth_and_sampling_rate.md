---
title: "Setting audio bit depth and sampling rate"
date: 2012-05-17
forum: General Help
---

### Post by Yasashii on 2012-05-17
Hello. I'm a novice Linux user. I'm currently using Xubuntu 12.04

I like getting the best I can out of my hardware. This includes sound. In windows it was quite simple. I just went to the audio settings and set the bit depth and sampling rate to the biggest values available.

With Xubuntu though, it's a little more tricky. There is no advanced settings in the graphic configurator. That means I have to look for bit depth and sampling rate in a configuration file. The thing is, I don't know which one exactly.

If anyone could tell me which one it is and which lines I have to modify, I would be grateful.

---

### Post by forrestcupp on 2012-05-17
Do you want this for playback or recording?

---

### Post by Yasashii on 2012-05-17
Preferably both. I might need to do some recording in the future.

---

### Post by forrestcupp on 2012-05-17
I don't know about playback, but usually with recording, you set that in whatever recording software you're using.

---

### Post by Rodney9 on 2012-05-17
In recording with Audacity you have quality settings in Preferences, see screenshot below.

If you want you could use Ubuntu Studio, quote from their [site]("http://ubuntustudio.org/") - 
> 
Real Time Kernel - Ubuntu Studio uses the Ingo Molnar PREEMPT patched real-time kernel (for more information about the real-time kernel, take a look at the RTWiki FAQ). This helps to reduce the amount of latency, which is extremely beneficial for audio work. The low levels of latency that can be achieved in Linux with the real-time kernel can also surpass those available under Windows and Mac.

System Configuration - The Ubuntu Studio team has already configured the Ubuntu Studio system to help maximize the real-time kernel. The user is included in the audio group and the limits.conf file is specifically configured.

JACK Sound System - Along with the ubiquitous Pulse Audio sound server, the powerful JACK sound server is also included in Ubuntu Studio. Both are already configured to work well together. 

Rodney

---

### Post by Yasashii on 2012-05-17
Yeah ok but can anyone tell me how to change the system-wide bit depth and sampling rate?

---

### Post by pbrane on 2012-05-17
The playback sample rate is a function of the file format the audio is recorded in. The capture sample rate you can set in most recording software in ubuntu or by choosing a file format with the specs you want. Pulseaudio and ALSA initialize the sound card codec to the number of bits supported by the hardware codec itself. If you have a 22 bit codec then that's what you get. Now the type of audio file format has an effect on this. e. g., WAV files are mostly 16 bit.

Basically the settings you want to set are probably in **/etc/pulse/daemon.conf**. 

```

grep "sample-rate" /etc/pulse/daemon.conf

```
if it comes back with a semi-colon at the beginning it is disabled. You can remove the semi-colon to enable that sample-rate.

To have the changed config take effect restart pulseaudio by simply issuing this in a terminal
```

pulseaudio --kill

```
Pulseaudio will restart itself by default. If you have changed that you can do this
```

pulseaudio --kill
pulseaudio --start

```

here is a link that might help
[https://wiki.archlinux.org/index.php/PulseAudio#1._Determine_soundcards_in_the_system]("https://wiki.archlinux.org/index.php/PulseAudio#1._Determine_soundcards_in_the_system")

---

### Post by forrestcupp on 2012-05-17
> **Yasashii said:**
> Yeah ok but can anyone tell me how to change the system-wide bit depth and sampling rate?

As far as I know, you can set volumes and balances, but there is no system-wide settings for bit depth and sampling rates. Your system will just play sounds at whatever bit depth and sampling rate the individual multimedia files were recorded at. As far as recording, it's the same story. You can set the input volume, but you will always set the bit depth and sampling rate from within whatever recording software you are using.

There is no system-wide setting for those.

---

### Post by Yasashii on 2012-05-17
Ok thanks, will see if that works

---

### Post by pbrane on 2012-05-17
> **Yasashii said:**
> 
...
Also, even if a file is recorded with 24 bits and 96000 hz (max values for my sound card), it will still be resampled to the system-wide settings. As far as I can remember it's 16 bit and 48000 hz by default (which is what I want to change).

True, all sounds would be resampled to the system default rate. 48KHz probably.

have a look at
```

man pulse-daemon.conf

```

---

### Post by pbrane on 2012-05-17
> **forrestcupp said:**
> As far as I know, you can set volumes and balances, **but there is no system-wide settings** for bit depth and **sampling rates**. Your system will just play sounds at whatever bit depth and sampling rate the individual multimedia files were recorded at. As far as recording, it's the same story. You can set the input volume, but you will always set the bit depth and sampling rate from within whatever recording software you are using.

There is no system-wide setting for those.

**/etc/pulse/daemon.conf** at least for the sample rate.

EDIT: default-sample-format controls the default bit-depth.

---

### Post by Yasashii on 2012-05-17
> **pbrane said:**
> True, all sounds would be resampled to the system default rate.

Thank you for confirming. Forrest's post actutally had me doubt myself to the point I edited the whole post to avoid embarrassing myself. As far as I knew, I would be right for sure if we were talking about Windows but with Linux I wasn't so sure after reading his post.

Anyway, thanks for the name of the file. I'm going to edit it right away.

edit: 
> To have the changed config take effect restart pulseaudio

Rebooting the system will have the same effect, right?

---

### Post by forrestcupp on 2012-05-17
Sorry for the bad info. It doesn't make sense that you could play a wav that had a sample rate of 48000 and your system would resample it to 44100 because that's the system-wide setting.

---

