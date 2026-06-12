---
title: "Selecting USB Headphone/mic under Natty?"
date: 2011-04-29
forum: General Help
---

### Post by jerome1232 on 2011-04-29
Ok so I have a USB Headphone/microphone, I recall it working automatically in 10.10

When I plug it in it seems to be recognized but the sound indicator doesn't give it as an option to use. How can I go about trouble shooting this. All information I came across search was incredibly outdated.

I primarily intend to use this with mumble, a voice conference client. It uses pulse audio and doesn't see the headset either.

```
jeremy@Farewell:~$ dmesg | tail
[   51.533232] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[   55.940008] eth0: no IPv6 routers present
[45400.900011] usb 2-10: new full speed USB device using ohci_hcd and address 4
[45401.135431] input: C-Media USB Headphone Set   as /devices/pci0000:00/0000:00:0b.0/usb2/2-10/2-10:1.3/input/input7
[45401.135529] generic-usb 0003:0D8C:000C.0005: input,hidraw4: USB HID v1.00 Device [C-Media USB Headphone Set  ] on usb-0000:00:0b.0-10/input3
[45401.413050] usbcore: registered new interface driver snd-usb-audio
[45444.208961] usb 2-10: USB disconnect, address 4
[45705.270014] usb 2-10: new full speed USB device using ohci_hcd and address 5
[45705.730421] input: C-Media USB Headphone Set   as /devices/pci0000:00/0000:00:0b.0/usb2/2-10/2-10:1.3/input/input8
[45705.730498] generic-usb 0003:0D8C:000C.0006: input,hidraw4: USB HID v1.00 Device [C-Media USB Headphone Set  ] on usb-0000:00:0b.0-10/input3

```

---

### Post by ard on 2011-04-29
I have the exact same problem.  USB headphone worked fine in 10.10, but in 11.04, in "Sound Preferences", it shows up under the "Hardware" tab, but not the "Input" or "Output" tabs.  

Also, if I hit the "Test Speaker" button under the "Hardware" tab with the Headphone selected, Sound Preferences crashes :(

---

### Post by jerome1232 on 2011-05-01
bump!

---

### Post by vulcanfk on 2011-05-01
I'm also affected by this.  There is a bug on launchpad for the "test speakers" issue here: [https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/736349](https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/736349)

However, I'm still looking into the USB headset issue...

---

### Post by colan on 2011-05-02
I opened a new bug for this over at [https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/775345](https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/775345).  Please confirm and add more information if you have it.  Thanks!

---

### Post by Ghilteras on 2011-05-02
same problem here, with my usb headset (0d8c:000c) after upgrading to natty, when I plug them in I get:


cannot find the slot for index 0 (range 0-0), error: -16
cannot create card instance 0
snd-usb-audio: probe of 2-2:1.0 failed with error -5

---

### Post by jerome1232 on 2011-05-09
I just wanted to report with a recent update, the headphones began to appear in sound preferences as "audio adapter"

The USB headset is functioning although mumble seems to be wrecking unrelated havoc with my Unity Interface.

I'm unsure how to contribute to that bug report, particularly since the issue seems to have been fixed with a patch. Any guidance?

---

### Post by Ghilteras on 2011-05-10
this bug tracks the issue 

[https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/775345](https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/775345)

but there wasnt any recent update of pulseaudio or alsa in the last few days so I doubt they did anything as for now, the bug got just confirmed, but noone of the team has answered yet so the best we can do is track the bug and give information as soon as a dev will post

---

### Post by Freiberg on 2011-06-02
Well, there seems to be an update of some kind, as the headset now immediately appears in sound preferences for both input and output.  However, this does little good, because even with it selected, it refuses to play any sound.

---

### Post by stinkeye on 2011-06-02
> **Freiberg said:**
> Well, there seems to be an update of some kind, as the headset now immediately appears in sound preferences for both input and output.  However, this does little good, because even with it selected, it refuses to play any sound.

Install/run alsamixer and check your volume settings.
I frequently have to unplug and plug back in my headphones after boot

---

