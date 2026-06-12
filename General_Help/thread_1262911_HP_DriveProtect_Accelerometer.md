---
title: "HP DriveProtect Accelerometer"
date: 2009-09-10
forum: General Help
---

### Post by LubindaMaim on 2009-09-10
Ubuntu is keen on supporting my hardware but it decided to use an accelerometer used by the hard-drive for the hp data protect thing as a joystick/controller. Thus interfering with games I play unless I find a perfectly flat surface. 

I have no idea how to remedy this and if possible without disabling the accelerometer altogether cose the hp data protect thing seems quite useful.

Thanks.

---

### Post by LubindaMaim on 2009-09-10
bump

---

### Post by kaspar42 on 2009-10-23
I have the same problem here. 
In Windoze it is a simple matter of deleting the accelerometer in the device manager. Surely something similar must be possible in Ubuntu 9.04?

---

### Post by P4man on 2009-10-23
ROFL. Sorry i cant really help, but I have to say thats funny. So you can actually use your harddisk as joystick? in a way thats awesome. well, at least if you can disable it.

---

### Post by LubindaMaim on 2009-10-23
neverball is quite interesting to play like this :) , the sensitivity seems to have been reduced in karmic though so not quite as annoying.

---

### Post by P4man on 2009-10-23
LOL.

Anyway, perhaps have a look at the output of ```
lsmod
```. See if you can identify the driver being used to drive your.. "joydrive" and then blacklist it? I have no idea if it will impact the security features of driveprotect though. I would guess the drive autonomously parks the head if it detects a drop, but I cant be certain.

BTW, for a wiimote, the kernel module used is "uinput". Figured it might be the same as both work with accelerometers...

---

### Post by LubindaMaim on 2009-10-23
This is what I got highlighted the interesting parts,

```
#Module                  Size  Used by
binfmt_misc            10220  1 
ppdev                   8232  0 
snd_hda_codec_idt      72976  1 
snd_hda_intel          31880  2 
snd_hda_codec          87584  2 snd_hda_codec_idt,snd_hda_intel
bridge                 56384  0 
stp                     3012  1 bridge
bnep                   15168  2 
snd_hwdep               9352  1 snd_hda_codec
snd_pcm_oss            44704  0 
snd_mixer_oss          18976  1 snd_pcm_oss
sha256_generic         10816  0 
snd_pcm                93160  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           3460  0 
arc4                    2144  2 
snd_seq_oss            33440  0 
ecb                     3296  3 
snd_seq_midi            8192  0 
snd_rawmidi            27360  1 snd_seq_midi
iwlagn                124832  0 
iwlcore               133248  1 iwlagn
cryptd                  8008  0 
aes_x86_64              8992  767 
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                60608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
aes_generic            28480  1 aes_x86_64
cbc                     4224  765 
iptable_filter          3872  0 
mac80211              210104  2 iwlagn,iwlcore
lp                     11908  0 
snd_timer              26992  2 snd_pcm,snd_seq
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               65260  0 
ip_tables              21200  1 iptable_filter
x_tables               25832  1 ip_tables
snd                    77096  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              109144  3 iwlagn,iwlcore,mac80211
soundcore               9088  1 snd
snd_page_alloc         10928  2 snd_hda_intel,snd_pcm
[B]hp_accel               12480  0 
lis3lv02d               9312  1 hp_accel
input_polldev           4720  1 lis3lv02d[/B]
btusb                  14260  2 
videodev               43360  1 uvcvideo
psmouse                57124  0 
v4l1_compat            16804  2 uvcvideo,videodev
nvidia              10316904  38 
v4l2_compat_ioctl32    13344  1 videodev
dm_crypt               14888  1 
led_class               5256  2 iwlcore,hp_accel
serio_raw               6596  0 
joydev                 13088  0 
parport                40528  2 ppdev,lp
usbhid                 43968  0 
video                  23612  0 
output                  3680  1 video
intel_agp              32816  0 
r8169                  38884  0 
mii                     6368  1 r8169
```

but how do i blacklist it?

EDIT: nvm forgot about google.

---

### Post by P4man on 2009-10-23
You can read here how:
[http://ubuntuforums.org/showthread.php?t=166624](http://ubuntuforums.org/showthread.php?t=166624)

Im not sure which of them you should blacklist, probably only lis3lv02d . Have a look here:

[http://www.mjmwired.net/kernel/Documentation/hwmon/lis3lv02d](http://www.mjmwired.net/kernel/Documentation/hwmon/lis3lv02d)

---

### Post by LubindaMaim on 2009-10-23
Blacklisting lis3lv02d doesn't solve it somehow :-k, but hp_accel does. Problem solved :-D.

---

### Post by kaspar42 on 2009-10-23
> **P4man said:**
> You can read here how:
[http://ubuntuforums.org/showthread.php?t=166624](http://ubuntuforums.org/showthread.php?t=166624)

Im not sure which of them you should blacklist, probably only lis3lv02d . Have a look here:

[http://www.mjmwired.net/kernel/Documentation/hwmon/lis3lv02d](http://www.mjmwired.net/kernel/Documentation/hwmon/lis3lv02d)

sudo modprobe -r lis3lv02d

Solved it for me :)

---

### Post by P4man on 2009-10-23
> **kaspar42 said:**
> sudo modprobe -r lis3lv02d

Solved it for me :)

until your next boot...

---

### Post by kaspar42 on 2009-10-23
> **P4man said:**
> until your next boot...

Sure, but as it is only occasionally disruptive, I decided not to remove it permanently.

---

