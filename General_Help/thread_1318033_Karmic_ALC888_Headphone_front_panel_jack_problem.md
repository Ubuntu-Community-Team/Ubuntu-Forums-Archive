---
title: "Karmic ALC888 Headphone front panel jack problem"
date: 2009-11-07
forum: General Help
---

### Post by baytuni on 2009-11-07
Hi all. I've upgraded Karmic from Jaunty and now the front panel jack output is not working.  Embedded mic and speakers work but I could not try the mic jack since I have no external mic around.
I use ```
options snd-hda-intel model=auto
``` in alsa-base config file. I tried the other alternatives in /usr/share/doc/alsa-base/driver/HD-Audio-Models.txt.gz but "auto" option is the best so far at least the embedded speakers and mic works. 


Here are my system specifications, all help will be appreciated. Thanks

Hardware:
Nec Versa M370SE
Realtek ALC888 Azalia 

Drivers:
Pulse audio Version: 1:0.9.19-0ubuntu4
alsa-base Version: 1.0.20+dfsg-1ubuntu5



alsa-base config file:

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
# Power down HDA controllers after 10 idle seconds
options snd-hda-intel power_save=10 power_save_controller=N
options snd-hda-intel model=auto
```

---

### Post by baytuni on 2009-11-07
Problem is solved by changing this value "options snd-hda-intel model=targa-dig" in /etc/modprobe.d/alsa-base.conf. It came to me in my dream :D

---

### Post by juliobahar on 2009-11-28
I'm sorry but this didn't work for me actually I didn't have the line
"options snd-hda-intel model=targa-dig"

I added it to the file "/etc/modprobe.d/alsa-base.conf", but when I change the connector drop down list to analog headphone headphone sound goes off. But Analog Output seems to work fine only with the speakers' back audio jack. Front Jacks aren't working in Karmic with and intel chipset sound. 

Btw it was working so fine after upgrading from jaunty to karmic, yet somewhere when I upgraded to the kernel to 2.6.31-15 I guess this could have something to do with it. Not sure actually.

---

### Post by juliobahar on 2009-11-28
Just discovered that the kernel has nothing to do with the front headphone jack not working. By reverting back to the previous kernel that used to make the headphones work I still can't make use of my earsets...

---

