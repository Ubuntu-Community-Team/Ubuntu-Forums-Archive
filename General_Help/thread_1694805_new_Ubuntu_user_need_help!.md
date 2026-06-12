---
title: "new Ubuntu user need help!"
date: 2011-02-24
forum: General Help
---

### Post by pilulelilule on 2011-02-24
Hi Guys,

I noticed that my headphones dont work and regular speakers do. However when i switch to windows headphones work fine. Before approaching for help i did read the forum and found out that headphones might be muted and to run  alsamixer on the terminal. Result is the following master is 100/100 pmc is 100/100, S/PDIF & S/PDIF Default PCM is 00 and i dont know how to change that if i even need to. Sound card is on default.

my system:
intel pentium core duo t4500
sound: Conexant cx20671 SmartAudio HD
Ubuntu: 10.10

**Ubuntu runs great everything else works fine.

---

### Post by amsterdamharu on 2011-02-24
Could you press alt + F2, then type pavucontrol and click run.

Under the tab input devices you can set volume of the microphone and or mute it. You should be able to hear yourself blowing in the microphone for example.

Just in case that doesn't work could you post the output of the following commands?
```
cat /proc/asound/card0/codec#* | grep Codec
cat /etc/modprobe.d/alsa-base.conf
```

To execute the command(s) you can press alt + F2, type gnome-terminal and click run. Then copy one command and paste it in the terminal (black screen that showed up after you clicked run). Use the mouse to paste commands in the terminal.
Then you can select all the text in the terminal, right click and select copy. When pasting it here please wrap it in code tags: &#91;code][COLOR=Red]Your pasted stuff[/COLOR]&#91;/code]

---

### Post by pilulelilule on 2011-03-01
p { margin-bottom: 0.21cm; }  This is what i got in the terminal



[code]# autoloader aliases
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
 options snd-usb-caiaq index=-2
 options snd-usb-ua101 index=-2
 options snd-usb-us122l index=-2
 options snd-usb-usx2y index=-2
 # Ubuntu #62691, enable MPU for snd-cmipci
 options snd-cmipci mpu_port=0x330 fm_port=0x388
 # Keep snd-pcsp from being loaded as first soundcard
 options snd-pcsp index=-2
 # Keep snd-usb-audio from beeing loaded as first soundcard
 options snd-usb-audio index=-2 [code]

---

### Post by pilulelilule on 2011-03-01
hey thanks i ran pavucontrol, didnt work so i got it installed in the terminal. However when i opened it i didnt see anywhere headphones at all.

---

### Post by pilulelilule on 2011-03-01
when i run alsamixer it also doesn't show microphone

---

### Post by franchoy on 2011-03-02
go to Sytem/Control Center/Sounds ---click output tab, select your device. the headphones are not auto detected on ubuntu 10.10

---

### Post by pilulelilule on 2011-03-02
That still does not solve the problem the output device is selected! "Internal Audio Analog Stereo" How do i fix this problem and enable my headphones to work in Ubuntu there must be a way??:confused:

---

### Post by vivek.pandey on 2011-03-02
in the sytem->preferences->sound-> output-> connectors did you try changing it to analog headphones instead of analog speakers?

---

### Post by pilulelilule on 2011-03-02
in sound-->output i have no option to change the controllers for the headphones at all

---

### Post by vivek.pandey on 2011-03-02
> **pilulelilule said:**
> in sound-->output i have no option to change the controllers for the headphones at all

well there is a connector option in output tag which has stuffs like analog speakers, analog output and analog headphones i was referring to that.. be sure to see once more and its connector option

---

### Post by pilulelilule on 2011-03-02
I appreciate your help! So i am right now in Sound Preferences in the "output" there are no options for me, however in the "hardware" there are several options Device "internal audio 1input/1output analog stereo duplex with six options


[LIST=1]
[*]off
[*]Analog Stereo Input
[*]Digital Stereo Duplex (IEC958)
[*]Digital Stereo (IEC958)Output+Analog Stereo Input
[*]Analog Stereo Output
[*]Analog Stereo Duplex
[/LIST]
Currently it is set on Analog Stereo Duplex

---

### Post by pilulelilule on 2011-03-02
I have also installed pavucontrol previously

---

