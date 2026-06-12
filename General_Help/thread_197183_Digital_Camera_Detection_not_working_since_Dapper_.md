---
title: "Digital Camera Detection not working since Dapper upgrade"
date: 2006-06-15
forum: General Help
---

### Post by kingmonkey on 2006-06-15
Hi all,

I upgraded to Dapper and since then ubuntu doesnt like my camera. This is what happens:

:?: I plug my camera in and switch it on
:?: the "A carmera has been detected" thing pops up then I click Import
:?: then it says "Loading camera drivers from '/usr/lib/gphoto2/2.1.6'..." and just stays there without my camera being detected.

dmesg shows:
:?: usb 1-3: new full speed USB device using ohci_hcd and address 2

Any pointers welcome?

EDIT: This might be usefull for you...

```
$ gthumb --import-photos
GTK Accessibility Module initialized
Bonobo accessibility support initialized
ALSA lib confmisc.c:672:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1072:(snd_func_refer) error evaluating name
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3962:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2102:(snd_pcm_open_noupdate) Unknown PCM default

```

EDIT2:

```
$ gphoto2 --auto-detect
Model                          Port
----------------------------------------------------------
Kodak DX7440                   usb:
Kodak DX7440                   usb:001,006
 
```

EDIT:

gphoto2 seems to be working fine so maybe the problem is with gthumb (or ALSA???)

EDIT:

dont think alsa is to blame because those error messages come up even if i only start gthumb. Gthumb always goes into a zombie when I close it down/kill it. How do you get rid of a zombie?

EDIT:

Oh I dont know, gphoto2 doesnt seem to work now.

---

### Post by kingmonkey on 2006-06-15
Seems to be working now since the kernel update today. Im using the amd64 kernel btw.

---

