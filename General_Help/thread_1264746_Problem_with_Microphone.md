---
title: "Problem with Microphone"
date: 2009-09-12
forum: General Help
---

### Post by PeEllAvaj on 2009-09-12
I recently bought a microphone headset, and I can't figure out how to get it to work.  USB mics (tried it with a dedicated, and with a webcam) show up in the devices list, and work fine, but ones plugged into the analog port on the front or back of my computer don't.

I'm using ALSA for my audio system (alsa-base 1.0.18.dfsg-1ubuntu8).  lshw lists my audio device as follows:

*-multimedia                                                                                                                                                                   
          description: Audio device                                                                                                                                                 
          product: MCP55 High Definition Audio                                                                                                                                      
          vendor: nVidia Corporation                                                                                                                                                
          physical id: 6.1                                                                                                                                                          
          bus info: pci@0000:00:06.1                                                                                                                                                
          version: a2                                                                                                                                                               
          width: 32 bits                                                                                                                                                            
          clock: 66MHz                                                                                                                                                              
          capabilities: pm msi ht bus_master cap_list                                                                                                                               
          configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2 module=snd_hda_intel

The way I test my mic is to open audacity, select an audio device, try to record something, and repeat.

Any help would be appreciated.

---

### Post by khelben1979 on 2009-09-12
I have for a long time (several years) experienced the same problem. I have a brother which managed to get it to work and he made it work by installing [pulse audio]("http://en.wikipedia.org/wiki/Pulse_audio").

I just decided to get a usb headset with inbuilt sound and never bothered to use a mic in the analog port myself.

---

### Post by PeEllAvaj on 2009-09-12
More information:

The devices that show up as options (I have tried them all):
[LIST]
[*]ALSA: HDA NVidia: ALC883 ANalog (hw:0,0)
[*]ALSA: HDA NVidia: ALC883 Digital (hw:0,1)
[*]ALSA: HDA NVidia: ALC883 Analog (hw:0,2)
[*]ALSA: spdif
[*]ALSA: default
[*]OSS: /dev/dsp
[*]OSS: /dev/dsp1
[/LIST]

---

### Post by khelben1979 on 2009-09-12
I suggest you install Pulse audio then. Search for it in [Synaptic Package Manager]("http://en.wikipedia.org/wiki/Synaptic_package_manager").

---

### Post by PeEllAvaj on 2009-09-12
I've installed pulseaudio and restarted the entire system.  I've also been reading up on how pulseaudio works, but I'm definitely missing something.

Nothing seems to have changed, all of my programs still list only ALSA sound devices, and I have read about per-application audio control, but I see no new controls in kmix.  Am I supposed to install some new pulseaudio control panel?

Thanks.

---

### Post by khelben1979 on 2009-09-13
I dont know, let's hope some pulse audio expert can enter this thread. I have very limited experience on the subject.

---

### Post by elliotn on 2009-09-13
Same here I failed for long to configure ubuntu to work with mic

---

### Post by PeEllAvaj on 2009-09-13
Switching to pulse made my microphone work, but for some reason the levels are extremely low (inaudible unless I yell).  Is this a problem with the linux drivers, something I can change in pulse, or something I can change in alsa?

---

### Post by 3rdalbum on 2009-09-13
In order to use Pulseaudio, you need the "padevchooser" package. When you run the "padevchooser" program it adds an icon to your notification area, and from there you can route audio from applications to devices, and vice-versa.

Try turning the microphone's gain up; the regular volume control will be able to do this.

---

