---
title: "alsa proc/asound/cards"
date: 2006-05-14
forum: General Help
---

### Post by mrelectron on 2006-05-14
hi:

everytime i reboot (ubuntu dapper 6.06) my sound cards get swapped around. it does this everytime. how can the card settings be made permanent.  by default i use usb-audio. 

see below for example of /proc/asound/cards

thanks
mark

example:
reboot-1=================================================
cat /proc/asound/cards
0 [Headset        ]: USB-Audio - Logitech USB Headset
                     Logitech Logitech USB Headset at usb-0000:00:10.1-1, full speed
1 [V8235          ]: VIA8233 - VIA 8235
                     VIA 8235 with AD1980 at 0xd800, irq 201
=======================================================
reboot-2=================================================
cat /proc/asound/cards
0 [V8235          ]: VIA8233 - VIA 8235
                     VIA 8235 with AD1980 at 0xd800, irq 201
1 [Headset        ]: USB-Audio - Logitech USB Headset
                     Logitech Logitech USB Headset at usb-0000:00:10.1-1, full speed
=======================================================
reboot-3=================================================
cat /proc/asound/cards
0 [Headset        ]: USB-Audio - Logitech USB Headset
                     Logitech Logitech USB Headset at usb-0000:00:10.1-1, full speed
1 [V8235          ]: VIA8233 - VIA 8235
                     VIA 8235 with AD1980 at 0xd800, irq 201
=======================================================

tags: alsa configuration config ubuntu xubuntu setup .asoundrc alsa-utils
=======================================================

---

### Post by Sef on 2006-05-16
What Ubuntu version are you on?  If you are still on Warty, I would advise you to upgrade it as it is no longer supported.  Upgrade to either Breezy or Dapper, which will be stable 1 June.

---

### Post by mrelectron on 2006-05-16
[QUOTE=Sef]What Ubuntu version are you on?  If you are still on Warty, I would advise you to upgrade it as it is no longer supported.  Upgrade to either Breezy or Dapper, which will be stable 1 June.[/QUOTE]

hi 

thanks for the reply, as mentioned in my original post, i am running dapper 6.06. 

cheers
mark

---

### Post by Sef on 2006-05-16
> thanks for the reply, as mentioned in my original post, i am running dapper 6.06. 

Oopps.:oops: 

Let's try this:

From the terminal, copy and paste the results of your alsa-base:

sudo gedit /etc/modprobe.d/alsa-base

Also what is the default in sound (System > Preferences > Sound)

---

### Post by mrelectron on 2006-05-17
[QUOTE=Sef]Oopps.:oops: 
From the terminal, copy and paste the results of your alsa-base:
Also what is the default in sound (System > Preferences > Sound)[/QUOTE]

thanks sef, here is my alsa-base, i actually run xubuntu flight-seven so i don'thave a system > prefs > sound, how would i get the sound default from the command line?

cheers.
mark

# autoloader aliases
install sound-slot-0 modprobe snd-card-0
install sound-slot-1 modprobe snd-card-1
install sound-slot-2 modprobe snd-card-2
install sound-slot-3 modprobe snd-card-3
install sound-slot-4 modprobe snd-card-4
install sound-slot-5 modprobe snd-card-5
install sound-slot-6 modprobe snd-card-6
install sound-slot-7 modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd modprobe --ignore-install snd $CMDLINE_OPTS && { modprobe -Qb snd-ioctl32 ; : ; }
install snd-pcm modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { modprobe -Qb snd-pcm-oss ; : ; }
install snd-mixer modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { modprobe -Qb snd-mixer-oss ; : ; }
install snd-seq modprobe --ignore-install snd-seq $CMDLINE_OPTS && { modprobe -Qba snd-seq-midi snd-seq-oss ; : ; }

# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 modprobe --ignore-install saa7134 $CMDLINE_OPTS && { modprobe -Qb saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2

---

