---
title: "no sound on HP pavillion dv6, after install of 10.04."
date: 2010-05-01
forum: General Help
---

### Post by richardmalter on 2010-05-01
I had a similar problem with previous ubuntu release on the same machine: and again, I have no sound at all, looking for some advice please. Thank you.

---

### Post by P4man on 2010-05-01
have you checked its not simply a muted output?
to make sure press alt+f2 and enter

```
alsamixer
```

navigate it with your arrow keys, Make sure there is not a channel muted by accident, like PCM.

---

### Post by richardmalter on 2010-05-01
> **P4man said:**
> have you checked its not simply a muted output?
to make sure press alt+f2 and enter

```
alsamixer
```

navigate it with your arrow keys, Make sure there is not a channel muted by accident, like PCM.
Thanks. All channels at max. If I press F2 in the terminal that opens for ALSA, I have two sound cards:
0 [Intel          ]: HDA-Intel - HDA Intel          &#9474;            
                   HDA Intel at 0xdd100000 irq 22 &#9474;            
&#9474; 1 [NVidia         ]: HDA-Intel - HDA NVidia         &#9474;            
&#9474;                      HDA NVidia at 0xd3000000 irq 1

Should I F6 select sound card choose one of these? or leave as default?

---

### Post by P4man on 2010-05-01
hmm. if you go system > preferences > sound > output i assume you have the same choice? What is it set to, and try the other one.

---

### Post by richardmalter on 2010-05-01
It displays Dummy Output that is selected and it seems I cannot deselect this. Below there is a L/R speaker drag bar that centred. Hardware lists nothing with no options. And input lists nothing with no options.

---

### Post by vibra on 2010-05-01
I have a system equals to yours, and I had no problem with sound. I had in past with 9.04/9.10. But after I format and install to 10.04, my sound works great.

sudo lshw:
description: Notebook
    product: HP Pavilion dv6 Notebook PC
    vendor: Hewlett-Packard


Can you provide us more info about your sound driver?

---

### Post by P4man on 2010-05-01
something else to try:

```
sudo apt-get install linux-backports-modules-alsa-lucid-generic
```

---

### Post by vibra on 2010-05-01
And, you can check out this page with some troubleshooting:
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

It helped me a lot in the past. ( I had such hard time troubleshouting my sound problems... O_o )

Because I have a system hp dv6, i will let  more info:

**model of sound card **
```
cat /proc/asound/card0/codec#* | grep Codec
```Codec: IDT 92HD75B3X5

 ******sound card list**
```
sudo aplay -l
```**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


I know this info doesn't help you directly but can help you to see what is wrong.

---

### Post by lidex on 2010-05-01
If audio is still out try this. Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=dell-m4 enable_msi=1  
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press F6 to select the correct soundcard.
Press F3 to show playback levels. F4 selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels.
Go to "System>Preferences>Sound" and make sure the correct soundcard is default.

---

### Post by richardmalter on 2010-05-02
Thanks everyone, am trying all the above, no luck yet, in the meantime:
Codec: IDT 92HD75B3X5
Codec: LSI ID 1040

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

**** List of PLAYBACK Hardware Devices ****
Home directory /home/taraduffy not ours.
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by richardmalter on 2010-05-02
More:
AlsaMixer v1.0.22

0 [Intel          ]: HDA-Intel - HDA Intel          &#9474;            &#9474;
&#9474;           &#9474;                      HDA Intel at 0xdd100000 irq 37 &#9474;            &#9474;
&#9474;           &#9474; 1 [NVidia         ]: HDA-Intel - HDA NVidia         &#9474;            &#9474;
&#9474;           &#9474;                      HDA NVidia at 0xd3000000 irq 38

Also, after trying all the above, my Sound Preferences are unchanged as above and still no sound  :-(

---

### Post by richardmalter on 2010-05-02
If this helps, when I get to the enter password and log in screen, if I select KDE (I was just experimenting) I get a start up sound. I dont know if that helps figure it. In the meanwhile I have not progressed.

---

### Post by P4man on 2010-05-02
How are you testing if sound works? if you are trying youtube or something, perhaps the problem is with flash. If you get a statup jingle, then the soundcard is working.

---

### Post by richardmalter on 2010-05-02
no start up jingle, that was only in KDE selected at log in screen. If I select Knome as usual there is no start-up jingle.. Sound Preferences: Input: there is no device listed, and Output I have Dummy Output. Hardware is empty.

Also Sound Recorder cannot detect my voice. DVD players have no sound, etc.

hmmm.

---

### Post by vibra on 2010-05-02
Looks like your sound card has not been detected by the system. I don't  know how to force the detection of sound cards. But see my alsa-base.conf file and compare to yours. Is there any difference?:

```
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
```

---

### Post by lidex on 2010-05-02
Have you tried the alsa-base.conf option I posted earlier? If that did not work remove it and add this line:
```
options snd-hda-intel model=hp-dv5 enable_msi=1

```
You have to reboot to see changes. BTW, this page is a great reference for HP laptops:
[http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html#installing]("http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html#installing")

Also what is the output of this command:
```
head -n 1 /proc/asound/card*/codec#*
```

Did you install alsa-backports as *P4man* suggested?

---

### Post by richardmalter on 2010-05-02
[FONT=monospace]Big thanks for continuing help, much appreciated :-)

head -n 1 /proc/asound/card*/codec#*     gives:
[/FONT]==> /proc/asound/card0/codec#0 <==
Codec: IDT 92HD75B3X5

==> /proc/asound/card0/codec#1 <==
Codec: LSI ID 1040

==> /proc/asound/card1/codec#0 <==
Codec: Nvidia ID a

==> /proc/asound/card1/codec#1 <==
Codec: Nvidia ID a

==> /proc/asound/card1/codec#2 <==
Codec: Nvidia ID a

==> /proc/asound/card1/codec#3 <==
Codec: Nvidia ID a
head -n 1 /proc/asound/card*/codec#*

I tried the first and the newly suggested alsa-base.conf option: 
[FONT=monospace]options snd-hda-intel model=hp-dv5 enable_msi=1[/FONT] (including deleting the last extra line added)

Also installed alsa-backports and checked that it installed.

vibra, thanks: my output looks identical to your except I have now added the last line:
options snd-hda-intel model=hp-dv5 enable_msi=1    [***my note: should this be dv6? - thats the model of the laptop**]

A possible helpful observation is that if I have Sound Recorder open, when I kill or open an application/window, even though I don't hear anything, the sound input bar of Sound Recorder detects the sound that I guess Ubuntu 'is' making as normal desktop sound theme.

Still no go . .. have read through the website suggested - seems we have tried most things on it(?)
Thanks again

---

### Post by lidex on 2010-05-02
Whenever you make changes in alsa-base.conf make sure to reboot and then go into alsamixer and check levels as alsa's default is muted. Here is a list of options reported to have worked with a dv6:
```
option snd-hda-intel model=dell-m4-1
options snd_hda_intel model=hp-dv5
options snd-hda-intel model=dell-m4-3 enable_msi=1
*these next 4 together*
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=hp-dv5
options snd-hda-intel enable_msi=1
```

[the model options can be used with or without msi and multiple options can reside on one line]

---

### Post by richardmalter on 2010-05-02
I am assuming I am reading Alsamixer graphs correctly: they are all up in the red portion.

But S/PDIF &  S/PDIF & Bass Speaker have no bar and just 00 listed.

The selected card is:
 Card: HDA Intel                                                                                            &#9474;
&#9474; Chip: IDT 92HD75B3X5

Just thought worth listing all this (last line is current attempt):
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
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=hp-dv5

---

### Post by lidex on 2010-05-02
Try gnome-alsamixer and make sure they are enabled in 'Edit>Sound Card Properties' and also on the soundcard tab.

---

### Post by richardmalter on 2010-05-02
Some boxes were unticked in Sound Properties, I ticked them, then got:

** (gnome-alsamixer:2623): WARNING **: gam_toggle_get_state (). No idea what to do for mixer element "Mic Jack Mode"!

** (gnome-alsamixer:2623): WARNING **: gam_toggle_get_state (). No idea what to do for mixer element "IEC958 Playback Source"!

** (gnome-alsamixer:2623): WARNING **: gam_toggle_get_state (). No idea what to do for mixer element "Mic Jack Mode"!

** (gnome-alsamixer:2623): WARNING **: gam_toggle_set_state (). No idea what to do for mixer element "Mic Jack Mode"!

** (gnome-alsamixer:2623): WARNING **: gam_toggle_get_state (). No idea what to do for mixer element "IEC958 Playback Source"!

** (gnome-alsamixer:2623): WARNING **: gam_toggle_set_state (). No idea what to do for mixer element "IEC958 Playback Source"!


Thanks for all the advice and time. Does anyone know what I can do at this stage?

---

### Post by olwe on 2010-05-19
Also having Realtek ALC272 probs on a Toshiba L455 on Kubuntu 10.04

How do you install "alsa backports?" I've seen links (click here) but then the browser wants to know which app to run it in...

I have sound from cranking up alsamixer to the max, but the System Settings for audio says "audio playback HDA Intel ALC272 not working."

---

### Post by lidex on 2010-05-20
> **olwe said:**
> Also having Realtek ALC272 probs on a Toshiba L455 on Kubuntu 10.04

How do you install "alsa backports?" I've seen links (click here) but then the browser wants to know which app to run it in...

I have sound from cranking up alsamixer to the max, but the System Settings for audio says "audio playback HDA Intel ALC272 not working."

Update your kernel:
```
sudo apt-get update
sudo apt-get upgrade
```
Now reboot so we can work with the latest kernel.
Install alsa backports:
```
sudo apt-get install linux-backports-modules-alsa-lucid-generic
``` Reboot again.

---

