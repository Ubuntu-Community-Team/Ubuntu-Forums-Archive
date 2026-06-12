---
title: "No headphones or microphone in Toshiba laptop"
date: 2010-09-26
forum: General Help
---

### Post by decoherence on 2010-09-26
I have a Toshiba Satellite A660-056 which works beautifully except that the built in mic and the headphone jack don't work.

For the microphone, no input device is listed in the Sound Preferences control panel.

When I plug in headphones, the built-in speakers go quiet but nothing goes through the headphones.

Here's the info

```
uname -a
Linux satelliteoflove 2.6.32-24-generic #43-Ubuntu SMP Thu Sep 16 14:17:33 UTC 2010 i686 GNU/Linux

```

```
sudo lshw -C sound
  *-multimedia            
       description: Audio device
       product: High Definition Audio Controller
       vendor: nVidia Corporation
       physical id: 0.1
       bus info: pci@0000:01:00.1
       version: a1
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:16 memory:b3000000-b3003fff
  *-multimedia
       description: Audio device
       product: 5 Series/3400 Series Chipset High Definition Audio
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 05
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:22 memory:b8400000-b8403fff

```

let me know if there's anything else that'd be useful. Thanks for any help!

---

### Post by lidex on 2010-10-02
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

### Post by decoherence on 2010-10-02
Thanks for the tip lidex! Didn't know about that.

[http://www.alsa-project.org/db/?f=f32e9e24efbddd61b9c8eb74ffd248864d8ccba3](http://www.alsa-project.org/db/?f=f32e9e24efbddd61b9c8eb74ffd248864d8ccba3)

I would guess that it has something to do with having both nvidia and intel sound hardware, but that's just a guess.

Thanks for taking a look!

---

### Post by lidex on 2010-10-03
I want you to follow the alsa-upgrade-script link in my sig. There you will find instructions to upgrade your alsa version to 1.0.23.
Please do that and report your results.

---

### Post by decoherence on 2010-10-03
> **lidex said:**
> I want you to follow the alsa-upgrade-script link in my sig. There you will find instructions to upgrade your alsa version to 1.0.23.
Please do that and report your results.

Thanks, my headphones are working now! But the built-in microphone is still dead. Alsamixer recognizes three recording channels: front mic boost, mic boost and capture. They're all turned up and unmuted.

If I do 'select sound hardware' and choose the nvidia hardware i'm told that the device has no capture controls so i guess that's just for hdmi.

In case it helps, I've run alsa-info again. Here's the output [http://www.alsa-project.org/db/?f=8cc79b6884ef5b2e8bce10a125f04dfed10560b4](http://www.alsa-project.org/db/?f=8cc79b6884ef5b2e8bce10a125f04dfed10560b4)

Thanks again for your help!

---

### Post by lidex on 2010-10-03
> **decoherence said:**
> Thanks, my headphones are working now! But the built-in microphone is still dead. Alsamixer recognizes three recording channels: front mic boost, mic boost and capture. They're all turned up and unmuted.

If I do 'select sound hardware' and choose the nvidia hardware i'm told that the device has no capture controls so i guess that's just for hdmi.

In case it helps, I've run alsa-info again. Here's the output [http://www.alsa-project.org/db/?f=8cc79b6884ef5b2e8bce10a125f04dfed10560b4](http://www.alsa-project.org/db/?f=8cc79b6884ef5b2e8bce10a125f04dfed10560b4)

Thanks again for your help!

This is a newer codec, so don't have much info on it. A few bugs reported on Dell machines. Have you tried 'Sound Recorder' to see if you're getting any input? Also helpful is pulse audio volume control and volume meter. 
First, for mic problem, check this.
**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install:
```
sudo apt-get install gnome-alsamixer
```

Then go to 'Sound Preferences' to select and unmute your mic in 'Input' tab.
Make sure you have selected a profile with 'duplex' or 'analog input' for the correct sound device on the 'Hardware' tab.
Use Pulse Audio Volume Control (pavucontrol) to unlock stereo sliders for the mic in 'Input Devices' tab. Drag the right slider down to zero. The mic is a mono device.

From alsa documentation:
> Capture Problems
~~~~~~~~~~~~~~~~
The capture problems are often because of missing setups of mixers.
Thus, before submitting a bug report, make sure that you set up the
mixer correctly.  For example, both "Capture Volume" and "Capture
Switch" have to be set properly in addition to the right "Capture
Source" or "Input Source" selection.  Some devices have "Mic Boost"
volume or switch.

When the PCM device is opened via "default" PCM (without pulse-audio
plugin), you'll likely have "Digital Capture Volume" control as well.
This is provided for the extra gain/attenuation of the signal in
software, especially for the inputs without the hardware volume
control such as digital microphones.  Unless really needed, this
should be set to exactly 50%, corresponding to 0dB -- neither extra
gain nor attenuation.  When you use "hw" PCM, i.e., a raw access PCM,
this control will have no influence, though.

---

### Post by Mr_G on 2010-11-21
I have the same problem the speakers work but the  headphones do not.
Below is the alsainfo script o/p I m currently using a toshiba satellit l640d
[http://www.alsa-project.org/db/?f=55f610f2b34a3f16af456d2f777fbd17d7aee591](http://www.alsa-project.org/db/?f=55f610f2b34a3f16af456d2f777fbd17d7aee591)

---

### Post by deepaknet on 2011-10-15
> **lidex said:**
> Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

I am facing this issue. My laptop has built-in speaker but no mike and hence using headphones (that gives mike). Sound plays both in built in and headphone. When I use microphone in sound recorder it appears to be receiving some sound. But when I play it there is no sound.

ALSA INFO:

[http://www.alsa-project.org/db/?f=07834e83cdeed69aec78466111bea7edd10beb64](http://www.alsa-project.org/db/?f=07834e83cdeed69aec78466111bea7edd10beb64)

---

