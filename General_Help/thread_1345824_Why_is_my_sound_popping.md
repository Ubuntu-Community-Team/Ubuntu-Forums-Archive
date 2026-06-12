---
title: "Why is my sound popping?"
date: 2009-12-04
forum: General Help
---

### Post by JoeyF on 2009-12-04
When i first turned the comp on this morning  i got a small pop when it was loading.

ANd also when i first played a song with whatever the default player is.


Any idea? could it be drivers?

I have a Emachines w3650.

Thanks,

---

### Post by JoeyF on 2009-12-04
It only does it every now and then BTW. I didn't even notice it until last night when i played  a Youtube video.

---

### Post by JoeyF on 2009-12-04
[CENTER]**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0[/CENTER]

---

### Post by eriktheblu on 2009-12-04
I find that reducing the system volume often correct this for me.

---

### Post by JoeyF on 2009-12-04
[http://www.emachines.com/products/products.html?prod=W3650](http://www.emachines.com/products/products.html?prod=W3650)

Is there any way i can add a sound card?

---

### Post by BinaryFeast on 2009-12-04
The popping sound is most likely related to a power management setting. I had the same problem and the following solved it for me:

Open up the terminal (or press alt+f2) and type

```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```

comment out the last line with a "#" if it looks like this:

```
# Power down HDA controllers after 10 idle seconds
options snd-hda-intel power_save=10 power_save_controller=N
```

so that it says:

```
# Power down HDA controllers after 10 idle seconds
# options snd-hda-intel power_save=10 power_save_controller=N
```

After a reboot (or logout/login may be enough) the popping sound disappeared for me.

---

