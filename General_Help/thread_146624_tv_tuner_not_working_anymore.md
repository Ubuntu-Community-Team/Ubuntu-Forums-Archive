---
title: "tv tuner not working anymore"
date: 2006-03-18
forum: General Help
---

### Post by antcodd on 2006-03-18
Hi I just booted into linux to try and fix the problem with my tv tuner having terrible receptiion in linux, but it wasnt working at all today it says cannot find file /dev/video1.

So I tried reinserting the module and I get this error message

```
# sudo modprobe -v em28xx
insmod /lib/modules/2.6.12-10-k7/kernel/drivers/media/video/em28xx/em28xx.ko
FATAL: Error inserting em28xx (/lib/modules/2.6.12-10-k7/kernel/drivers/media/video/em28xx/em28xx.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```

this must have worked before because i just went back aways through the command history to what i must have used before.

The only thing I have done since it was last working is installed updates which included a new kernel. I have also enabled sli in the nvidia config but that shouldnt do that should it?

I am now running 2.6.12-10-k7

I have tried reinstalling the v4l package.

I am running Breezy 32bit
AMD Athlon 64 3500+
2x Nvidia Geforce 6800gt in SLI
Tv tuner is Pinnacle PCTV 100e PAL I think (doesnt say the model number on it)

PS: is there any useful docs on how to getting tvtuners going i had to follow a whole bunch of tutorials and edit them for my needs and in general do a huge amount of google searchs as I am not very experienced at linux.

Edit: oops I mean breezy
here is the relevant info from dmesg as far as I can tell

```
[4294804.506000] em28xx: Unknown symbol ir_codes_em_terratec
[4294804.506000] em28xx: Unknown symbol v4l_printk_ioctl
[4294804.506000] em28xx: disagrees about version of symbol tveeprom_hauppauge_analog
[4294804.506000] em28xx: Unknown symbol tveeprom_hauppauge_analog
[4294804.506000] em28xx: Unknown symbol ir_codes_em_pinnacle_usb
[4297032.829000] em28xx: Unknown symbol ir_codes_em_terratec
[4297032.829000] em28xx: Unknown symbol v4l_printk_ioctl
[4297032.829000] em28xx: disagrees about version of symbol tveeprom_hauppauge_analog
[4297032.829000] em28xx: Unknown symbol tveeprom_hauppauge_analog
[4297032.829000] em28xx: Unknown symbol ir_codes_em_pinnacle_usb

```

---

### Post by antcodd on 2006-03-20
Anyone know how to fix this?

---

### Post by sedrak on 2007-11-14
I had installed em28xx driver for Pinnacle pctv hybrid tunner which was working without
sound on my Gutsy system. But when I tryed to solve a problem with sound the video also
stoped to operate. I have reinstalled again firmware and the driver  from 

hg clone [http://mcentral.de/hg/~mrec/v4l-dvb-experimental](http://mcentral.de/hg/~mrec/v4l-dvb-experimental)

but respons on

modprobe em28xx is

FATAL: Error inserting em28xx (/lib/modules/2.6.22-14-generic/kernel/drivers/media/video/em28xx/em28xx.ko): Unknown symbol in module, or unknown parameter (see dmesg)

while 
dmesg | grep em28xx 
gives

[11067.548000] em28xx: Unknown parameter `(tuner'

What happened? Can anybody help me?
Thanks
  Ara:):)

---

