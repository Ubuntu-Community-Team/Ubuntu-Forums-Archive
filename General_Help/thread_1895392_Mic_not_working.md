---
title: "Mic not working"
date: 2011-12-14
forum: General Help
---

### Post by kkelly77 on 2011-12-14
The microphone on my Targa Traveller 1534 has never worked since I switched to Ubuntu 10.04 from Windoze Vista. I have tried a number of solutions listed on the forum as well as on the net but I have had no luck with any of them.

I was wondering if anyone could offer some advice/help with this. Some of the solutions I've tried can be found - 
[Here]("http://ubuntuforums.org/showthread.php?t=1781200&highlight=targa")

[Here]("http://ubuntuforums.org/showthread.php?t=1517261&page=2")

[Here]("http://ubuntuforums.org/showthread.php?t=1379587&highlight=microphone&page=2")

[Here]("https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules")

I've attached a couple of screenshots of my sound preferences. You can see there is no microphone listed. However, if I change the Profile under Settings For The Selected Device, the mic is listed. But this makes no change to the fact it still does not work. Thanks for the help.

K.

---

### Post by kkelly77 on 2011-12-27
Bumping thread. Need help with this problem.

---

### Post by xc3RnbFO8P on 2011-12-27
Try:
Settings for the selected device >  Analog Stereo Duplex

---

### Post by kkelly77 on 2011-12-27
> **Ringi said:**
> Try:
Settings for the selected device >  Analog Stereo Duplex

Tried that setting. Mic still does not work.

---

### Post by xc3RnbFO8P on 2011-12-27
> **kkelly77 said:**
> Tried that setting. Mic still does not work.
Did you try in Terminal:
> alsamixer

---

### Post by kkelly77 on 2011-12-27
> **Ringi said:**
> Did you try in Terminal:

All levels in Alsamixer are unmuted and set to max.

---

### Post by xc3RnbFO8P on 2011-12-27
Do you have screenshot of alsamixer window (F5)

---

### Post by kkelly77 on 2011-12-27
> **Ringi said:**
> Do you have screenshot of alsamixer window (F5)

Attached

---

### Post by xc3RnbFO8P on 2011-12-27
One solution is to install GNOME ALSA Mixer (Ubuntu Software Center)

and move the Mic balance slider all the way to the left (or right)

---

### Post by kkelly77 on 2011-12-27
> **Ringi said:**
> One solution is to install GNOME ALSA Mixer (Ubuntu Software Center)

and move the Mic balance slider all the way to the left (or right)

According to SW Center, I already have it installed. How do I start Gnome Alsa Mixer?

EDIT: I've found it!! Also, I have Pulse Audio installed too. Could these be conflicting with one another?

---

### Post by xc3RnbFO8P on 2011-12-27
> **kkelly77 said:**
>  Could these be conflicting with one another?

No!

Try the sliders and turn the other Capture on

---

### Post by kkelly77 on 2011-12-27
> **Ringi said:**
> No!

Try the sliders and turn the other Capture on

No luck :(

---

### Post by pretty_whistle on 2011-12-27
My mic doesn't work either.

I have noted that the only place it has worked for me is in Ubuntu 11.04.

But I now have Lubuntu and no mic!

Weird.

---

### Post by guestolo on 2011-12-27
@[kkelly77]("http://ubuntuforums.org/member.php?u=1013436")

What line/ lines did you add to the end of 
/etc/modprobe.d/alsa-base.conf ?

---

### Post by kkelly77 on 2011-12-27
> **guestolo said:**
> @[kkelly77]("http://ubuntuforums.org/member.php?u=1013436")

What line/ lines did you add to the end of 
/etc/modprobe.d/alsa-base.conf ?

I was just about to post that :D

```
options snd-hda-intel model=targa-8ch-dig
```I entered this line while trying to use one of the other solutions posted on the forum. I also tried changing
model= targa-dig
model= targa-2ch-dig

No luck with either one. When I changed back to targa-8ch-dig, there were settings for Internal Mic in GNOME Alsa Mixer. These are unmuted and set to highest level.

---

### Post by guestolo on 2011-12-27
Not sure if this will work, but worth a try

I have a different laptop, alsamixer shows
Card: HDA Intel
Chip: Realtek ALC663
I had problems with  Microphone with Ubuntu 11.10
No sound on Skype, sound recorder, etc...

what did work for me 
I removed any line I added to the end of 
/etc/modprobe.d/alsa-base.conf

with the following
```
options snd-hda-intel model=auto
```Rebooted, haven't had any other problems with Microphone
That's my story, not sure if you will have the same results

---

### Post by kkelly77 on 2011-12-27
> **guestolo said:**
> Not sure if this will work, but worth a try

I have a different laptop, alsamixer shows
Card: HDA Intel
Chip: Realtek ALC663
I had problems with  Microphone with Ubuntu 11.10
No sound on Skype, sound recorder, etc...

what did work for me 
I removed any line I added to the end of 
/etc/modprobe.d/alsa-base.conf

with the following
```
options snd-hda-intel model=auto
```Rebooted, haven't had any other problems with Microphone
That's my story, not sure if you will have the same results

I tried that already as it was one of the possible solutions I found. I tried it again anyway, still no luck.

---

### Post by guestolo on 2011-12-27
Different laptop again, same chip, may give results, just putting it out there
Take a look at Reply#2 from Kami

[http://forum-en.msi.com/index.php?topic=137959.0](http://forum-en.msi.com/index.php?topic=137959.0)

---

### Post by kkelly77 on 2011-12-27
> **guestolo said:**
> Different laptop again, same chip, may give results, just putting it out there
Take a look at Reply#2 from Kami

[http://forum-en.msi.com/index.php?topic=137959.0](http://forum-en.msi.com/index.php?topic=137959.0)

Unfortunately that (and the other solutions) listed on that forum didn't work either. 

I'm using Skype test call to check if the mic is working. When the test call is meant to be playing back whatever the mic has picked up, all I can hear is a 'hiss'.

---

### Post by kkelly77 on 2011-12-27
The last 3 lines of my alsa-base.conf file reads - 

```
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
options snd-hda-intel model=targa-8ch-dig
```Should I remove the lines

```
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
```


Full code of alsa-base.conf

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
options snd-hda-intel model=targa-8ch-dig
```

---

### Post by xc3RnbFO8P on 2011-12-27
How about installing Ubuntu 11.10, this dig think dosnt work in 10.04
[http://wiki.ubuntuusers.de/Soundkarten_konfigurieren/HDA?redirect=no]("http://wiki.ubuntuusers.de/Soundkarten_konfigurieren/HDA?redirect=no")

> options snd-hda-intel model=targa-dig - zusätzlich snd-hda-intel model=targa-dig in die /etc/modules eintragen

Achtung!

Funktioniert nicht unter Lucid Lynx! Empfohlene Vorgehensweise: Standard-Einstellungen beibehalten. 

---

### Post by kkelly77 on 2011-12-27
> **Ringi said:**
> How about installing Ubuntu 11.10, this dig think dosnt work in 10.04
[http://wiki.ubuntuusers.de/Soundkarten_konfigurieren/HDA?redirect=no](http://wiki.ubuntuusers.de/Soundkarten_konfigurieren/HDA?redirect=no)


I was going to wait for the next LTS to upgrade (12.04)

---

