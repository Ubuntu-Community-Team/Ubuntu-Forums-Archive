---
title: "Sound device changes on reboot"
date: 2006-06-08
forum: General Help
---

### Post by RikBlankestijn on 2006-06-08
Hi.

I've two soundcard in my computer, an onboard card and a soundblaster card. On every reboot of my computer ubuntu seems to use another soundcard.

For example I configure xmms to use device /dev/**dsp** and I can hear the music, but then on reboot I have to fix sound again and configure /dev/**dsp1**.
(I'd prefer the use of /dev/dsp because then it also response to the multimedia keys on my keyboard.)
Sound in gnome seems to work still on every reboot though, it's just that the /dev/dsp* seems to change.

How can it be that on reboot the devices changes and more important how can I fix it? 

Thanks in advance.

kind regards,
Rik

---

### Post by RikBlankestijn on 2006-06-12
anyone?

---

### Post by soze on 2006-06-12
I have sound from the mobo connected to my speakers and I also have a USB headset.

What I do is create a file called /etc/udev/rules.d/10-sound.rules
with the following:

```
# Rules for sound devices
# Motherboard sound will be /dev/mbdsp and /dev/audio
# Headset will be /dev/headsetdsp and /dev/audio1

BUS=="usb" SYSFS{product}=="Logitech USB Headset" KERNEL=="dsp*" SYMLINK="headsetdsp audio1"
BUS=="pci" DRIVER=="VIA 82xx Audio" KERNEL=="dsp*" SYMLINK="mbdsp audio"

```

This does not solve them bouncing back and forth between /dsp and /dsp1 (I'd love a solution to that one) but it does give you fixed device names you can use (/dev/mbdsp and /dev/headsetdsp)

---

### Post by RikBlankestijn on 2006-06-13
The fixed device names are already a step in the right direction for me. Thanks and hopefully someone will have a solution for the related issue.

---

### Post by RikBlankestijn on 2006-06-17
Anyone can help us solving the problem "bouncing back and forth between /dsp and /dsp1"?

---

### Post by RikBlankestijn on 2006-06-23
Can I somehow make the soundcard on my motherboard invisible to the kernel or something? I only want to use the soundblaster card and I'd say that would make things a lot easier. Other solutions are most welcome ofcourse.

---

### Post by dominikroblek on 2006-11-05
> **RikBlankestijn said:**
> Anyone can help us solving the problem "bouncing back and forth between /dsp and /dsp1"?

I have the same problem on Ubunto 6.06. I have only one sound card. After each reboot the sound card bounces from /dev/dsp1 to /dev/dsp or vice versa.

Since RealPlayer relies on the AUDIO environment variable, which points to the sound card device, I have to change it after each reboot in order to be able to hear sound from RealPlayer.

Does anybody know the solution to this problem?

---

### Post by jocko on 2006-11-05
> **RikBlankestijn said:**
> Can I somehow make the soundcard on my motherboard invisible to the kernel or something? I only want to use the soundblaster card and I'd say that would make things a lot easier. Other solutions are most welcome ofcourse.

One way is to prevent the driver module that is used by your onboard audio from loading:
```
sudo gedit /etc/modprobe.d/blacklist
```Add something like this to the end of the file:
```
blacklist [COLOR=Red]modulename[/COLOR]
```Another way is to prevent the onboard audio from becoming primary sound device:
```
sudo gedit /etc/modprobe.d/alsa-base
```Add a line looking like this to the end of the file:
```
options [COLOR=Red]modulename[/COLOR] index=-2
```Of course you should change "[COLOR=Red]modulename[/COLOR]" to the name of the actual module.
A third way that should work would be to inactivate the onboard sound in bios.

---

