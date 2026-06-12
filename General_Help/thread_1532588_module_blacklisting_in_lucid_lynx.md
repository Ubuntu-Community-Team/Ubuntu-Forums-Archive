---
title: "module blacklisting in lucid lynx"
date: 2010-07-16
forum: General Help
---

### Post by freshw on 2010-07-16
Hi,

I tried to blacklist a module (snd) by putting the corresponding line in /etc/modprobe.d/blacklist.conf (blacklist snd) and performing an 'update-initramfs -u', since this is the usual way to do so. But it just won't work.

I believe it might be a 10.4 issue.

Does anyone know how to blacklist modules in lucid lynx? I didn't find anything about this particular problem -- neither at the german nor the english ubuntu forums (nor a casual google search).

Any hints? Ani links?

Many thanks in advance!
Freshw

---

### Post by bodhi.zazen on 2010-07-16
That is where it goes.

What problem are you having , what how-to are you following to solve it.

Did you try this syntax :

```
blacklist snd_hda_intel
```

Can you post the syntax you used ?

---

### Post by freshw on 2010-07-16
It's a very old laptop computer with a minimal ubuntu installation (console only) on which some sound stuff made trouble (according to /var/log/syslog). And since I don't need sound on that machine I decided to blacklist everything sound-relevant.

[LEFT]It seemed useful to blacklist snd. So I put the line
[/LEFT]
[CENTER][LEFT]```
blacklist snd
```
into /etc/modprobe.d/blacklist.conf (should be the correct syntax) and updated the initramfs as described above. But after reboot snd was still there and active (according to lsmod).

Now I blacklisted snd_via82xx instead and it worked just fine. lsmod shows no more sound modules.

Hence it's not a 10.4 issue as I thought (sorry for that) and my problem is solved.

One question remains: Why doens't blacklisting snd take effect?

Thanks again.
Freshw


[/LEFT]
[/CENTER]

---

### Post by bodhi.zazen on 2010-07-16
> **freshw said:**
> One question remains: Why doens't blacklisting snd take effect?
[CENTER][LEFT] 
Thanks again.
Freshw


[/LEFT]
[/CENTER]


The module is not "snd" it is snd_additional_syntax

In your case "snd_via82xx"

---

### Post by freshw on 2010-07-16
Well, on my machine the output of lsmod (before blacklisting snd_via82xx) looked like that:
```

Module                  Size  Used by
dm_crypt               11331  0
arc4                    1153  2
snd_via82xx            20058  0
gameport                9089  1 snd_via82xx
snd_ac97_codec        100646  1 snd_via82xx
ac97_bus                1002  1 snd_ac97_codec
rt73usb                22434  0
snd_pcm                70662  2 snd_via82xx,snd_ac97_codec
crc_itu_t               1371  1 rt73usb
snd_timer              19098  1 snd_pcm
rt2500usb              18141  0
snd_page_alloc          7076  2 snd_via82xx,snd_pcm
rt2x00usb               9703  2 rt73usb,rt2500usb
snd_mpu401_uart         5617  1 snd_via82xx
rt2x00lib              27509  3 rt73usb,rt2500usb,rt2x00usb
snd_rawmidi            19056  1 snd_mpu401_uart
led_class               2864  1 rt2x00lib
yenta_socket           20408  0
snd_seq_device          5700  1 snd_rawmidi
mac80211              205146  2 rt2x00usb,rt2x00lib
rsrc_nonstatic         10015  1 yenta_socket
ppdev                   5259  0
snd                    54148  7 snd_via82xx,snd_ac97_codec,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
via686a                10986  0
cfg80211              126517  2 rt2x00lib,mac80211
pcmcia_core            32964  2 yenta_socket,rsrc_nonstatic
soundcore               6620  1 snd
i2c_viapro              5573  0
lp                      7028  0
parport_pc             25962  0
shpchp                 28820  0
parport                32635  3 ppdev,lp,parport_pc
uvesafb                22297  0
fbcon                  35102  71
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  1
via_agp                 5310  1
vgastate                8961  1 vga16fb
pata_via                7272  3
agpgart                31724  1 via_agp

```

As you can see there are several modules beginning with "snd", particularly one just named snd. Blacklisting snd_via82xx was the right thing to do, since it makes all the other "snd..."-modules disappear. I certainly do realize that.

But the last question still remains. Why couldn't I blacklist snd for example? Maybe it's because modules aren't allowed to be in use by others in order to being removable?

Sudden inspiration! I think this might be it.

It's funny how asking a question sometimes helps you looking at something a bit clearer yourself.

Thanks!
Freswh

---

