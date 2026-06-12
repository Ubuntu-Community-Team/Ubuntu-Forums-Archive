---
title: "sound wont init on boot after running out of disk space"
date: 2009-12-03
forum: General Help
---

### Post by Argh de tromp on 2009-12-03
I don't know if this is the cause, but
I ran out of disk space, coudn't login and things broke...

After enlarging the system partition, some problems sorted themselves out,
but I lost some settings and the nvidia graphics driver. Reinstalling that fixed it and compiz worked perfectly. 
 
But sound dosen't quite work right and now fails to init on boot.
running sudo /sbin/alsa force-reload will make it load, but sometimes I have to run it several times to make both soundcards to be recognized. once loaded they work well.

There were also two freezes with corrupted screen after login.

I am using both sound devices side by side:
Intel HDA for regular sound set as index 0
M-audio 1010LT for studio work set as index 1
mixed through external mixer

I am also using  an M-audio 1x1 usb midi interface and a usb keyboard

I just got a korg nanokontrol (usb) and changed to a usb wheelmouse from a ps/2 mouse because I needed the middle button

the nanokontrol prevents the 1010LT from starting if it's plugged in at boot.
plugging it in after boot, it works fine.
I haven't tried changing the mouse back again.

I still haven't got the boot screen working right yet, so I think other things may be screwed up.

Ubuntu Studio AMD_64
Asus m2n-mx se plus
AMD Athlon 64X2 5200+
2 gig ram
kernel 2.6.24-25rt
Gnome 2.22.3

---

### Post by Argh de tromp on 2009-12-06
Update: see below.

---

### Post by Argh de tromp on 2009-12-06
Update:

It seems to be the extra usb devices are displacing the audio devices, 
and nothing to do with running out of disk space.

I get this error in dmesg:

[   41.884342] hda_codec: Unknown model for ALC662, trying auto-probe from BIOS...
[   41.888750] usbcore: registered new interface driver snd-usb-audio
[   42.017670] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-rt/sound/alsa-driver/acore/init.c:174: cannot find the slot for index 1 (range 0-1), error: -16
[   42.017791] ICE1712: probe of 0000:01:06.0 failed with error -12

I had set these lines in /etc/modprobe.d/alsa_base:

options snd_hda_intel index=0
options snd_ice1712 index=1

I thought those entries reserved those indexes so that other devices won't take them.

I would like to have them load as:

snd_hda_intel as index=0
snd_ice1712 as index=1
then,
Midiman 1x1 as 3
Korg nanokontrol as 4

I'm still pretty new at linux, so I'm still trying to figure out these config files.

I managed to get the midiman working on my own thanks to these forums!

Any help would be welcome!

Thank You!

---

