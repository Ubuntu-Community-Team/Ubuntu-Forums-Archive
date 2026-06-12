---
title: "upgrade from natty to oneiric"
date: 2011-10-15
forum: General Help
---

### Post by Ofloo on 2011-10-15
For starters the upgrade failed eventually did it myself using apt-get dist-upgrade from console screens cause the gui was totally ******, all seems to be working from what i can tell however my headset witch used to work just by plugging it in plantronics 995 doesn't show in the volume control center as an output device, .. i mean i can see it in lsusb and from what i can tell it is being used in lsmod as well cause the sound module is loaded and it's in use, .. now it does list as hardware but when i go to output to select it doesn't list neither does the microphone, .. anyone any suggestions, .. 

```
[ 5420.904054] usb 4-2: new full speed USB device number 4 using uhci_hcd
[ 5421.851793] input: Plantronics Wireless Audio Plantronics Wireless Audio as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.3/input/input15
[ 5421.852480] generic-usb 0003:047F:D955.0009: input,hiddev0,hidraw2: USB HID v1.01 Device [Plantronics Wireless Audio Plantronics Wireless Audio] on usb-0000:00:1d.2-2/input3
[ 5421.992239] usbcore: registered new interface driver snd-usb-audio

```

```
$ lsmod | grep -i usb
snd_usb_audio         118064  0 
snd_usbmidi_lib        25371  1 snd_usb_audio
snd_rawmidi            30547  1 snd_usbmidi_lib
snd_pcm                96755  4 snd_usb_audio,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_hwdep              13668  2 snd_usb_audio,snd_hda_codec
snd                    68266  16 snd_usb_audio,snd_usbmidi_lib,snd_rawmidi,snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_pcm,snd_hwdep,snd_timer
usbhid                 47198  0 
hid                    95463  1 usbhid

```

PS: who's bright idea was it to make it so that unity was integrated within the desktop completely !

---

### Post by CharlesA on 2011-10-15
Hi,

If you are asking for support, it might be a bit better to leave the rant out of it. If you want to talk about your experience with Ubuntu, check out the [Testimonials forum]("http://ubuntuforums.org/forumdisplay.php?f=103").

---

### Post by Jeinhor on 2011-10-15
> **Ofloo said:**
> For starters the upgrade failed eventually did it myself using apt-get dist-upgrade from console screens cause the gui was totally ******, all seems to be working from what i can tell however my headset witch used to work just by plugging it in plantronics 995 doesn't show in the volume control center as an output device, .. i mean i can see it in lsusb and from what i can tell it is being used in lsmod as well cause the sound module is loaded and it's in use, .. now it does list as hardware but when i go to output to select it doesn't list neither does the microphone, .. anyone any suggestions, .. 

```
[ 5420.904054] usb 4-2: new full speed USB device number 4 using uhci_hcd
[ 5421.851793] input: Plantronics Wireless Audio Plantronics Wireless Audio as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.3/input/input15
[ 5421.852480] generic-usb 0003:047F:D955.0009: input,hiddev0,hidraw2: USB HID v1.01 Device [Plantronics Wireless Audio Plantronics Wireless Audio] on usb-0000:00:1d.2-2/input3
[ 5421.992239] usbcore: registered new interface driver snd-usb-audio

```

```
$ lsmod | grep -i usb
snd_usb_audio         118064  0 
snd_usbmidi_lib        25371  1 snd_usb_audio
snd_rawmidi            30547  1 snd_usbmidi_lib
snd_pcm                96755  4 snd_usb_audio,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_hwdep              13668  2 snd_usb_audio,snd_hda_codec
snd                    68266  16 snd_usb_audio,snd_usbmidi_lib,snd_rawmidi,snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_pcm,snd_hwdep,snd_timer
usbhid                 47198  0 
hid                    95463  1 usbhid

```

PS: who's bright idea was it to make it so that unity was integrated within the desktop completely !

Oh I would just LOVE to help you after your kind words. I get such an urge for just spending many hours of my spare time trying to figure out your problems and help you solve them, and I think most, if not all, of the Ubuntu power-users and developers do as well. Right now they're just gathering information, probably working on the biggest response post seen by man... stick in there, and you'll have your answer real real soon!

---

### Post by KnightLord on 2011-10-15
> **CharlesA said:**
> Hi,

If you are asking for support, it might be a bit better to leave the rant out of it. If you want to talk about your experience with Ubuntu, check out the [Testimonials forum]("http://ubuntuforums.org/forumdisplay.php?f=103").

True, but the level of frustration is still there.  The semblance of civility can be difficult to maintain when the operating system one has come to rely on turns against one, and locks out the only means of backing up critical / essential files for one's business.  

I can appreciate the donation of "spare" time, but this "upgrade" is demanding time I can not spare, and I'm sure I'm not alone in this.

If some of us come across as a bit terse, or abrasive, please understand that we might, in our own little worlds, have some reason for feeling that we've been betrayed, stabbed in the back, torpedoed by someone's idea of a "better idea".

Perhaps a few deep breaths on both sides would facilitate a more expedient solution to these problems?  One can only hope.

---

### Post by CharlesA on 2011-10-15
> **KnightLord said:**
> True, but the level of frustration is still there.  The semblance of civility can be difficult to maintain when the operating system one has come to rely on turns against one, and locks out the only means of backing up critical / essential files for one's business.  

I can appreciate the donation of "spare" time, but this "upgrade" is demanding time I can not spare, and I'm sure I'm not alone in this.

If some of us come across as a bit terse, or abrasive, please understand that we might, in our own little worlds, have some reason for feeling that we've been betrayed, stabbed in the back, torpedoed by someone's idea of a "better idea".

Perhaps a few deep breaths on both sides would facilitate a more expedient solution to these problems?  One can only hope.

I totally understand, I've had issues with breaking stuff and having to take the time to fix it. Just a friendly note there. :)

---

### Post by Ofloo on 2011-10-15
Thank you for the understanding

@Jeinhor
well i was just frustrated, but anyways already fixed it :p nice to know you're always willing to help :p

---

### Post by CharlesA on 2011-10-15
How were you able to get it working? Don't forget to mark the thread as solved from thread tools.

---

### Post by Ofloo on 2011-10-15
i know there is this select menu just can't seem to find it, i'll have a look at it tonight.

i got it working by manualy loading the usb modules then rebooting the system, cause the first time the modules weren't loaded i had to manually reloaded alsa, then still didn't work rebooted and everything loaded by it self, .. not sure if that was the reason but tried rebooting before but didn't do much. oh and i removed the old /etc/module.conf

---

### Post by Jeinhor on 2011-10-17
> **Ofloo said:**
> Thank you for the understanding

@Jeinhor
well i was just frustrated, but anyways already fixed it :p nice to know you're always willing to help :p

Trust me, I know the feeling. And I've probably posted a rant or two in this forum myself, so I guess I shouldn't say anything... but hey, I just told you people were looking into it, right? ;)

---

