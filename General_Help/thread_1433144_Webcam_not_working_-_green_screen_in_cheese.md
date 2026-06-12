---
title: "Webcam not working - green screen in cheese"
date: 2010-03-18
forum: General Help
---

### Post by Phear46 on 2010-03-18
Hi, i have a microsoft lifecam vx1000 (i know, im a traitor!) ive plugged it into my eeepc901 and loaded cheese. it works fine. the laptop runs ubuntu NBR 9.10

Ive plugged it into my desktop, installed cheese and im getting a green display with some static on the top. Not a green tint, just a green block if you know what i mean.

My desktop is running ubuntu 9.10. Ive fiddles around with all the settings in gstreamer-proerties and i cant figure it out, nothing helps. Ive done some searching and all the help i can find seems to relate to ubuntu 8.x

Any help is appreciated, im at a total loss atm :/ 

Thanks
Nathan

---

### Post by spiderbatdad on 2010-03-18
```
lsmod
``` will list the module loaded for the device. I'm thinking, run lsmod on the machine where the came works, then the same on the desktop machine. See if the same module is loaded. If not load it with sudo modprobe <module_name>

---

### Post by Phear46 on 2010-03-18
ok, done that. It seems i was missing uvcvideo on my desktop. so i did 'sudo modprobe uvcvideo' and now its listed in lsmod the same as it is on the laptop.

The difference its made is.... theres now no static, just green. Im at a loss :/ im a noob at stuff like this :/

Thanks for the quick reply.
Nathan

---

### Post by spiderbatdad on 2010-03-18
I would think uvcvideo is the right choice. Try logging out and back in. Maybe even a restart.

---

### Post by Phear46 on 2010-03-22
tryed that spider, ive been away for the weekend, when i logged back on i noticed uvcvideo was no longer listed in lsmod. I tryed my cam, it didnt work. I 'modprobe uvcvideo' tryed the cam, didnt work, logged out and in, cam still didnt work. Heres what i have as the output of lsmod:

```

nathan@nathan-desktop:~$ lsmod
Module                  Size  Used by
uvcvideo               59080  0 
nls_utf8                1568  1 
isofs                  31620  1 
binfmt_misc             8356  1 
ppdev                   6688  0 
nfsd                  241100  9 
lockd                  67724  1 nfsd
nfs_acl                 2844  1 nfsd
auth_rpcgss            36576  1 nfsd
sunrpc                191712  8 nfsd,lockd,nfs_acl,auth_rpcgss
exportfs                4412  1 nfsd
snd_hda_codec_analog    59292  1 
snd_hda_intel          26920  2 
snd_hda_codec          75708  2 snd_hda_codec_analog,snd_hda_intel
arc4                    1660  2 
snd_usb_audio          84224  1 
snd_pcm_oss            37920  0 
ecb                     2524  2 
snd_usb_lib            16284  1 snd_usb_audio
snd_mixer_oss          16028  1 snd_pcm_oss
snd_hwdep               7200  2 snd_hda_codec,snd_usb_audio
snd_seq_dummy           2656  0 
snd_pcm                75296  4 snd_hda_intel,snd_hda_codec,snd_usb_audio,snd_pcm_oss
snd_seq_oss            28576  0 
rtl8187                50624  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  2 snd_usb_lib,snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
mac80211              181236  1 rtl8187
iptable_filter          3100  0 
snd_timer              22276  2 snd_pcm,snd_seq
ip_tables              11692  1 iptable_filter
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
led_class               4096  1 rtl8187
eeprom_93cx6            1916  1 rtl8187
snd                    59204  19 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_usb_audio,snd_pcm_oss,snd_mixer_oss,snd_hwdep,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
x_tables               16544  1 ip_tables
lp                      8964  0 
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
soundcore               7264  1 snd
nvidia               9586440  26 
parport                35340  2 ppdev,lp
gspca_sonixj           20796  0 
gspca_main             22812  1 gspca_sonixj
cfg80211               93052  2 rtl8187,mac80211
videodev               36736  2 uvcvideo,gspca_main
v4l1_compat            14496  2 uvcvideo,videodev
serio_raw               5280  0 
asus_atk0110            8252  0 
dm_raid45              84228  0 
xor                    15620  1 dm_raid45
ohci1394               29900  0 
usbhid                 38208  0 
ieee1394               86596  1 ohci1394
sky2                   46560  0 
floppy                 54916  0 
intel_agp              27484  0 
agpgart                34988  2 nvidia,intel_agp


```

does that help anyone? I think i need to wipe all the cam drivers and start a fresh, but im not sure how. The only think i can get atm is a green screen and a static bar at the top. But like i say, cam worked straight off when i plugged it into my ubuntu laptop(NBR).

Thanks,
Nathan

---

### Post by no2498 on 2010-03-22
you say you tried the v4l1 and v4l2 in gstreamer-properties
try your cam with ekgia softphone 
cheese keeps breaking my cam on 804 and 910
and i need to reset gstreamer-properties

try the preload like they do for skype put cheese in place of skype
you need the right one is 2 of them
1 for v4l1
and 1 for v4l2

hope that helps some

---

### Post by Phear46 on 2010-03-24
ekgia just notices the cam is there, it knows the cam is pluged in '/dev/video0' (or something similar) but i dont seem to be able to test the feed anywhere.

gstreamer-properties gives me the same result as cheese (4l1 just has a smaller green screen) and doesnt seem to be affected by cheese in anyway.

How do i know if i have the lastest kernel, or the kernel is the same on the laptop/desktop? A few threads on here suggest using 'KernelCheck' to update to the latest version but it doesnt work for me.

Thanks
Nathan

---

