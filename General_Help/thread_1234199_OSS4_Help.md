---
title: "OSS4 Help"
date: 2009-08-07
forum: General Help
---

### Post by jerome1232 on 2009-08-07
So I've had alot of problems with alsa not working correctly with pulseaudio, native pulse apps were great, alsa apps had scratchy sound and sometimes weren't even getting picked up by pulse somehow and got no sound at all.

I heard OSS4 is really good so I thought I'd try it out. I downloaded it from 4fronts site and installed the 64 bit .deb. Works Great. Sound is crystal clear and software mixing is working fantastic.

The only problem is OSS doesn't seem to recognize that I have a capture device (my mic). The old depreciated OSS did, alsa and pulseaudio worked with it too.

I'm not sure how to go about figuring this out, perhaps OSS4 doesn't have the driver for my card compelete?

Here is my card, and as far as I can work out the driver OSS4 is using.
```
sudo lshw -C multimedia
[sudo] password for jeremy: 
  *-multimedia            
       description: Audio device
       product: MCP67 High Definition Audio
       vendor: nVidia Corporation
       physical id: 7
       bus info: pci@0000:00:07.0
       version: a1
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list
       configuration: driver=oss_hdaudio latency=0 maxlatency=5 mingnt=2 module=oss_hdaudio

```

```
cat /usr/lib/oss/etc/installed_drivers 
oss_hdaudio #Nvidia High Definition Audio (MCP67)
oss_usb #Generic USB audio/MIDI device (BETA)

```

```
Version info: OSS 4.1 (b 1052/200903240621) (0x00040100) 
Platform: Linux/x86_64 2.6.28-14-generic #47-Ubuntu SMP Sat Jul 25 01:19:55 UTC 2009 (psion)

Number of audio devices:	6
Number of audio engines:	10
Number of mixer devices:	1


Device objects
 0: osscore0 OSS core services
 1: oss_hdaudio0 nVidia HD Audio interrupts=74224 (150060)
    HD Audio controller nVidia HD Audio
    Vendor ID    0x10de055c
    Subvendor ID 0x103c30cf
     Codec  0: Unknown (0x14f15051/0x103c30cf)
 2: oss_usb0 USB audio core services


Mixer devices
 0: High Definition Audio 0x14f1505 (Mixer 0 of device object 1)

Audio devices
HD Audio play pcm1                /dev/oss/oss_hdaudio0/pcm0  (device index 0)
HD Audio play pcm2                /dev/oss/oss_hdaudio0/pcm1  (device index 1)
HD Audio play pcm3                /dev/oss/oss_hdaudio0/pcm2  (device index 2)
HD Audio play spdifout            /dev/oss/oss_hdaudio0/spdout0  (device index 3)
HD Audio rec rec1                 /dev/oss/oss_hdaudio0/pcmin0  (device index 4)
HD Audio rec pcm3                 /dev/oss/oss_hdaudio0/pcmin1  (device index 5)

```

---

### Post by jerome1232 on 2009-08-11
Well it seems all it took was alot of experimental switch flipping and box checking to get it working. OSS4 is working fantastically for me now (is that a word?)

Here is a link to the thread that helped me in case anyone is interested. [http://4front-tech.com/forum/viewtopic.php?p=13084#13084](http://4front-tech.com/forum/viewtopic.php?p=13084#13084)

---

### Post by Arup on 2009-08-11
OSS 4 rules, the problem of weak mic in Skype got me to switch, I had to install Skype OSS version as well but the sound quality is like WOW! huge difference over ALSA. The recordings I thought were bad now come out in revealing details. Best method to install OSS4 trouble free is from Ubuntu's own help at [https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

---

### Post by jerome1232 on 2009-08-11
Thank you for that link, looking over makes me fairly confident I installed OSS4 correctly which I was slightly worried about.

But yeah, I'm loving OSS4! Sound has been the one weak link for me and oss4 does everything I need, including stream by stream control of sound volume (which is what I loved about pulse).

Really my only gripe was ALSA though, if wine would've made a plugin for for pulse audio I probably  would never have gotten fed up with everything and attempted the switch.

---

### Post by greggster on 2009-09-26
Thank you - pulse was using way too much CPU and sound was choppy.
Folks love opensource, but when stuff breaks some bail back to windows.
OSS - I'll support this $$ for sure.  Nerds only have so much time and opensource could benefit from more $$ to pay talented folks that otherwise work to pay the bills.  

Flash not working yet, else the rest is pleasant and I got my CPU back.

Thanks again for posting this.

---

### Post by levien on 2010-05-07
> **jerome1232 said:**
> Well it seems all it took was alot of experimental switch flipping and box checking to get it working. OSS4 is working fantastically for me now (is that a word?)

Here is a link to the thread that helped me in case anyone is interested. [http://4front-tech.com/forum/viewtopic.php?p=13084#13084](http://4front-tech.com/forum/viewtopic.php?p=13084#13084)

That link is no longer working unfortunately. I seem to have more or less the same problem. The microphone (which worked fine with ALSA) does not seem to be recognised by the OSS4 driver. The chipset is an Nvidia High Definition Audio (MCP78S), and ossinfo seems to show only one recording device:

```

HD Audio rec select1              /dev/oss/oss_hdaudio0/pcmin0  (device index 6)
HD Audio rec pcm4                 /dev/oss/oss_hdaudio0/pcmin1  (device index 7)

```

Any hints?

-L

---

