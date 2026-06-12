---
title: "double sound, headphone and laptop speakers"
date: 2012-04-30
forum: General Help
---

### Post by ninos_loves_u@hotmail.com on 2012-04-30
when i connect my headphones i still get sound from the laptop speakers where they should mute when i plug in the headphones and theres no way of muting the sound on the speaker while having it on headphone only...i have an acer aspire 6920g anyone?
thanks

---

### Post by Elzenbr8 on 2012-04-30
Simply, you need to reboot you system with your headphone connected. Or,
you can mute your speaker through sound settings before connecting your headphone.

---

### Post by ninos_loves_u@hotmail.com on 2012-04-30
it doesnt work..it mutes the phones too and rebooting the system with headphone doesnt do anything..

this is my alsa-base.conf
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
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2

# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2

---

### Post by gazzacbr on 2012-08-11
hi, i also have a 6920G with 12.04 (this is my first Ubuntu so dont have any previous) any update on this issue?
the sound is ALC889a which is the same as ALC885.
auto switching works fine on any windows and also on MAC  Snow and Lion (yes, same laptop).
i have speaker sound. if i reboot with headphones in i have sound through them.
either i can only have one or the other but cannot switch between them. just need auto switching.
if speakers are on then plugging headphones gives sound in both. i dont have any settings showing for headphones.
googled like crazy and i tried adding ...model=auto and acer-aspire to alsa-base.conf but that broke sound completely.

i did try a mod and updates for alsa and had a setting for auto switching in alsamixer but that really broke the sound and i had to complete restore :(

---

### Post by Boorhin on 2013-01-15
Hi,

I am having a similar problem. I recently updated my Ubuntu 12.04  pangolin and now I have both the sound in the speaker of the central unit and my headphones. It does not deactivate when the cable is plugged. I have a front and a back plug on the workstation. Nothing does. I must admit I assumed the updates will only do good and cannot remember all the packages I have recently installed. 
I installed pulseaudio thinking I could manually set it up for having only the output on the headphones. But it was without success. Here the Alsa info if somebody has a bit of time:
[http://www.alsa-project.org/db/?f=9e2eeb5e672955d1be9661f8cdd5b53ddcabfb27](http://www.alsa-project.org/db/?f=9e2eeb5e672955d1be9661f8cdd5b53ddcabfb27)

Thanks in advance,

Boorhin

---

### Post by scbingham on 2013-01-15
I had the same problem with my Advent 5301 12.04 32bit.
When I installed 12.04 64bit (I didn't realise it could run that) the problem with the speakers & headphones went away. :-)

Maybe it's worth seeing if that would work for you guys.
Type arch in a terminal window & see what it reports, x86_64 means you can run 64bit.

Worth a shot.

---

### Post by Boorhin on 2013-01-16
Nope my machine has always been under 64b OS

Boorhin

---

### Post by gazzacbr on 2013-01-19
hi, i had posted the answer for me somewhere but obviously not here :oops:

all i had to do was to update my kernel to 3.3.4 (check with uname -a)  thanks to someone who i cant remember
ok, it wasnt that easy and involved a lot of googling and terminal commands as usual but now i have plugin and unplug auto switching
hope that helps

---

### Post by Boorhin on 2013-01-21
It is not recommended to not use the generic kernel which is now 3.2.0-36.  With my Nvidia Quadro I try to stay in the lane because of all the problems it generates when I intend to be too fancy.
Former kernel worked fine.

It is possible that I have to reinstall the drivers, I had to do it  to get my Quadro working again because the grub thought I had another kernel or 2 i can't remember.

This is done by doing 

sudo update-grub

I unfortunately do not know how to reinstall the sound drivers yet but I will when I have 2 minutes


Boorhin

---

### Post by boregard on 2013-02-04
had the same problem and followed the info from this link[URL="https://help.ubuntu.com/community/SoundTroubleshootingProcedure"] https://help.ubuntu.com/community/SoundTroubleshootingProcedure  
[/URL]

---

### Post by Boorhin on 2013-02-11
Dear all, 

I don't know why there is a confusion with the pulseAudio volume control and the one from Unity and how the detection that I plugg jacks in the computer do not work anymore. However with alsamixer I could manually control the volume of the speaker inside the UC and thus solve part of the problem

Thanks for the link, 

Best 

Boorhïn

PS: I found also that [http://ubuntuguide.net/fix-sound-still-coming-from-speakers-after-plug-in-headphones-on-ubuntu-10-04](http://ubuntuguide.net/fix-sound-still-coming-from-speakers-after-plug-in-headphones-on-ubuntu-10-04)
That shows I should have an option jack sense. But this option does not appear

---

### Post by pschalkx on 2013-02-19
Hi all,

I also have a related issue with speakers and headphones after a clean install of 12.10 on my laptop:

- Before (with 10.04) I could switch between speakers and headphones via the sound applet in the menu. So when I selected the headphones the speakers were out and viceversa.

- Now I have either the speakers *and* the headphones or nothing. So I put on my headset but still bother everybody around through the speakers. There's no way to activate them separately in 12.10

Any ideas about where to look?

Thanks in advance.

Philip

---

### Post by Boorhin on 2013-02-19
Hi Philip,

Did you try to run alsamixer?
I have lost the autosense but with the alsamixer I manage to control what is muted individually. I see that in the backgrounds when I do some combination of mutes I have strange behaviours (like mute/unmute not considered). I also noted that the Alsa does not recognise the right audio chipset. I am still looking into it but lack time.
Best
Boorhin

---

