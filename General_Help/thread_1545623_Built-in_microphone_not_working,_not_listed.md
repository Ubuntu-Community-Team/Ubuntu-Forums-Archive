---
title: "Built-in microphone not working, not listed"
date: 2010-08-04
forum: General Help
---

### Post by titomax82 on 2010-08-04
Hi, I have a problem with my built-in microphone in ubuntu 10.04, it’s not listed in  mixers like other notebooks that have “anologue microphone 1 / 2 …”, I  have only Analogue microphone (that works only with external mic),  anlogue line-in and analogue input. Also I updated Alsa drivers to 1.0.23, but nothing changed….why my built-in microphone is not listed  by mixer, is not view at all?

Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio  Controller (rev 02), Packard Bell EasyNote MX67-P-023, Adi1986a

---

### Post by dragos240 on 2010-08-04
> **titomax82 said:**
> Hi, I have a problem with my built-in microphone in ubuntu 10.04, it’s not listed in  mixers like other notebooks that have “anologue microphone 1 / 2 …”, I  have only Analogue microphone (that works only with external mic),  anlogue line-in and analogue input. Also I updated Alsa drivers to 1.0.23, but nothing changed….why my built-in microphone is not listed  by mixer, is not view at all?

Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio  Controller (rev 02), Packard Bell EasyNote MX67-P-023, Adi1986a

If it's not listed in the mixer it may not have been picked up by the current kernel, it's an uncommon occurrence, but it happens. A quick search online of that model reveals that there have been issues with it in the past. You may find a module that you can compile manually to get it to work. Sorry about this.

---

### Post by titomax82 on 2010-08-04
i'm completely noob...ubuntu 10.04 lts, installed 10 days ago, is my first linux experience.... can you help me in how to solve this? or give me some links?

---

### Post by utilitytrack on 2010-08-04
[FONT=Droid Sans][FONT=Verdana, Arial, Tahoma]to **titomax82**
[/FONT]
[FONT=Verdana, Arial, Tahoma]Ok, please learn right ask questions. Put on forum more diagnostics info. Try it:

[/FONT]```
$ uname -r

$ dpkg -l alsa-*

$ lspci -nn | grep Audio

$ cat /proc/asound/card0/codec#0 | grep Codec

# hwinfo --sound

$ cat /etc/modprobe.d/alsa-base.conf

```[/FONT]
[FONT=Droid Sans][FONT=Verdana, Arial, Tahoma]and your PC/laptop model (it's you already gave us)
also recheck levels in alsamixer[/FONT][/FONT]

---

### Post by titomax82 on 2010-08-04
[FONT=Droid Sans]1) uname -r:
2.6.32-24-generic

2) dpkg -l alsa-*:
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Nome           Versione       Descrizione
+++-==============-==============-============================================
ii  alsa-base      1.0.22.1+dfsg- ALSA driver configuration files
un  alsa-headers   <not defined> (no description available)
un  alsa-oss       <not defined> (no description available)
ii  alsa-utils     1.0.22-0ubuntu ALSA utilities

3) lspci -nn | grep Audio:
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)

4) cat /proc/asound/card0/codec#0 | grep Codec:
Codec: Analog Devices AD1986A

5) hwinfo --sound:
09: PCI 1b.0: 0403 Audio device                                 
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_8086_27d8
  Unique ID: u1Nb.ZYYXjiFC7L8
  SysFS ID: /devices/pci0000:00/0000:00:1b.0
  SysFS BusID: 0000:00:1b.0
  Hardware Class: sound
  Model: "Intel 82801G (ICH7 Family) High Definition Audio Controller"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x27d8 "82801G (ICH7 Family) High Definition Audio Controller"
  SubVendor: pci 0x1631 "Packard Bell B.V."
  SubDevice: pci 0xc022 
  Revision: 0x02
  Driver: "HDA Intel"
  Driver Modules: "snd_hda_intel"
  Memory Range: 0xfebfc000-0xfebfffff (rw,non-prefetchable)
  IRQ: 29 (1083 events)
  Module Alias: "pci:v00008086d000027D8sv00001631sd0000C022bc04sc03i00"
  Driver Info #0:
    Driver Status: snd_hda_intel is active
    Driver Activation Cmd: "modprobe snd_hda_intel"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

6) cat /etc/modprobe.d/alsa-base.conf:
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2



Notebook: Packard Bell EasyNote MX67-P-023
Levels in alsa mixer are ok (maximum)...the real problem is that the built-in microphone can not be selected at all, there's only one "Analogue Microphone" which refers to external microphone jack
[/FONT]

---

### Post by utilitytrack on 2010-08-04
please give also ```
$ cat /proc/asound/devices
```

---

### Post by utilitytrack on 2010-08-04
Question: how to work playback on your laptop? Properly and without troubles?
[FONT='Courier New'][FONT=Verdana, Arial, Tahoma]
[/FONT][/FONT]

---

### Post by titomax82 on 2010-08-04
cat /proc/asound/devices:
  0: [ 0]   : control
  1:        : sequencer
  4: [ 0- 0]: hardware dependent
  5: [ 0- 1]: hardware dependent
 16: [ 0- 0]: digital audio playback
 17: [ 0- 1]: digital audio playback
 22: [ 0- 6]: digital audio playback
 24: [ 0- 0]: digital audio capture
 30: [ 0- 6]: digital audio capture
 33:        : timer


Audio playback works without problems

---

### Post by utilitytrack on 2010-08-05
> Audio playback works without problemsIt's good... 


Ok, as I see you had a AD1986A codec. Well, there is several ways to force work it properly. Generally, it can be make with help to change arguments that take the module before it will be loaded. The [FONT=Courier New]snd-hda-intel[/FONT] kernel module (you use it) takes certain model-specific arguments, full list of wich (with respect to AD1986A codec) you can see on [http://www.mjmwired.net/kernel/Documentation/sound/alsa/HD-Audio-Models.txt#238](http://www.mjmwired.net/kernel/Documentation/sound/alsa/HD-Audio-Models.txt#238). It's list of available args (8 items for your AD1986A), each of them may be suitable for your system (Packard Bell EasyNote MX67). 

Unfortunately I don't know exactly what need your system, but I suppose that is the [FONT=Courier New]3stack[/FONT] arg. To change it simple add this line to the end of file [FONT=Courier New]/etc/modprobe.d/alsa-base.conf[/FONT]
```
options snd-hda-intel model=3stack
```


Save and reboot. After go to terminal, run [FONT=Courier New]alsamixer[/FONT], type F4 and make the levels up ("Capture", "Mic Boost", "Internal Mic Boost" and may be some other). If these controls are present then run test record
```
$ arecord -vv -f cd -t wav sample.wav
```


If no success, simple try other argument ([FONT=Courier New]laptop-eapd[/FONT] for example), etc. Have experiment and you get luck! Please post here your impressions.

---

### Post by titomax82 on 2010-08-05
i tried them all and the last two entries gave some results: "samsung" and "samsung-p50"

the recorded sound is very disturbed...i'm trying with several level combinations between the normal audio control panel, alsamixer, gnome alsamixer etc... but it seems that even if i find the way to remove the background distorted rumor...even if i obtain silence, with recording capability still possible (level bar move as I speak), the recorded sound is still disturbed, while if i connect an external mic, internal mic mutes automatically and external mic works without any problem....any suggestion?

---

### Post by utilitytrack on 2010-08-06
Hello, make diagnostics such problems as distorted sound is difficult. A causes of it may be, for example, bad analog circuits (that is with high level of noise) or wrong levels settings in mixer. I'm not sure, but you can try add [FONT="Courier New"]position_fix=1[/FONT] and [FONT="Courier New"]power_save=0[/FONT] args in addition to [FONT="Courier New"]model=samsung[/FONT].

[SIZE="1"]PS
Don't forget run this for test record: [FONT="Courier New"]$ arecord -vv -f cd -t wav sample.wav[/FONT]

PPS
for setting up capture features properly you don't need use other programs except [FONT="Courier New"]alsamixer[/FONT] and [FONT="Courier New"]arecord[/FONT].[/SIZE]

---

### Post by titomax82 on 2010-08-06
UPDATE (sorry for my English):

I tried the "3stack" option, and built-in mic worked a little disturbed, but when an external mic was plugged the built-in mic was not excluded, so I had always sound disturbed; the microphone to use cannot be selected, there's only "Analogue Microphone" for both.

So I come back to the "samsung" option wich automatically exclude built-in mic when an external mic is plugged; as before, microphone cannot be selected (no matter), but built-in mic sound is more disturbed, so the only solution is "struggling with mixer".

I tried 4 mixer's option to achieve an acceptable recorded sound in the "arecord" test as suggested, and I found some surprises...strange behaviors:

1) "Mic": it doesn't change recorded volume, it only affects the volume voice is playbacked to speakers when talking to mic, so i set it to mute

2) "Mic Boost": it can boost volume, but create distortion; only 3 steps (33-66-100%), so I set it to 33% because a little boost is necessary because volume was too low

3) "Capture": this settings gives me lots of distortion, so I set it to 0 (but not mute or it silences all)

4) "Digital": surprisingly this settings affects mic volume, but it's responsible for background rumor, so, after many tries and combination with the other settings, I set it to 40%...and this combination of the 4 values gives me a reasonable result: voice is fully understandable, volume is sufficient (even if a little more would be better, but I have to balance it with the digital background rumor) and background rumor, even if present and audible, is tolerable and not frustrating.

This is my best result :) ... so, if no other suggestion, I think I can consider this case "SOLVED" - "in the best way possible" :)

Any other suggestions? If not I must thank you very much utilitytrack, you've been fast, precise and effective! Good work!

PS: utilitytrack...seen you're so good...take a look at this two threads:

1) [http://ubuntuforums.org/showthread.php?t=1546495](http://ubuntuforums.org/showthread.php?t=1546495)

2) [http://ubuntuforums.org/showthread.php?t=1541620](http://ubuntuforums.org/showthread.php?t=1541620)

---

### Post by utilitytrack on 2010-08-06
> 4) "Digital": surprisingly this settings affects mic volume, but it's responsible for background rumor 

I don't know what is mean "Digital" (it's some crank of ALSA developers), but how you describe it's absolutely normal behavior of analog circuits of capture, i.e. background noise grow up with rising the gain level.

PS
I'm very glad for you

---

