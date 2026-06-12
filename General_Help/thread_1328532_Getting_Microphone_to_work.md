---
title: "Getting Microphone to work ?"
date: 2009-11-16
forum: General Help
---

### Post by spikeyross on 2009-11-16
I have a Acer Aspire One Netbook

and i'm basically wanting the microphone to work and i don't know how to go about this ?

Currently it doesn't work 

Thanks Ross

---

### Post by arnab_das on 2009-11-16
go to sound preferences from System>Preference and see if the mic volume has been muted.

---

### Post by spikeyross on 2009-11-16
> **arnab_das said:**
> go to sound preferences from System>Preference and see if the mic volume has been muted.
Its not muted no
it only lets me choose 
"Internal Audio Analog System"

---

### Post by Giblet5 on 2009-11-16
Open a terminal window via Applications -> Accessories -> Terminal

Enter the command ```
alsamixer
```

Use the arrow keys to select the Microphone control and un-mute it via the 'm' key. Then use the up/down arrow to set the sensitivity.

You can do this via gui by installing the gnome-alsamixer package.

Rant: the default mixer in gnome on 9.10 sucks.

---

### Post by spikeyross on 2009-11-16
> **Giblet5 said:**
> Open a terminal window via Applications -> Accessories -> Terminal

Enter the command ```
alsamixer
```Use the arrow keys to select the Microphone control and un-mute it via the 'm' key. Then use the up/down arrow to set the sensitivity.

You can do this via gui by installing the gnome-alsamixer package.

Rant: the default mixer in gnome on 9.10 sucks.
I put both Front Mic and mic boost up full 
and screamed into it and i'm pretty sure it's still not working

---

### Post by Giblet5 on 2009-11-16
A lot of people praise [this guy's post]("http://ubuntuforums.org/showpost.php?p=7413520&postcount=16") on the Acer Aspire One and microphone troubles.

---

### Post by spikeyross on 2009-11-16
Right so basically the internal Microphone doesnt work
DAM

---

### Post by Giblet5 on 2009-11-16
That appears to be the consensus...

Keep watching the [AspireOne community]("https://help.ubuntu.com/community/AspireOne")'s postings on this. Problems like this don't last very long in the Linux world.

I bought a headset for my laptop, for use with Skype, because the microphone could not be enabled from Intrepid. Before I could actually get the headset from UPS, my microphone was supported via a patch. Your mileage will vary.

---

### Post by dvalenca on 2009-11-17
Be careful with the difference between the mic is not working or is not working in skype.
I'm using the Karmic Koala in my Aspire One, and I thought that wasn't work, and I saw
your tips and tryed again.

The mic is working, but not in Skype.

I tryed the sound recorder that cames in the Karmic and it recorded my voice.
I needed to use the artificial volume up, because it is to weak the capture.

Well, go to the alsamixer (in terminal), and tab two times to appear all...
With the arrows, put up all the options (I'm not sure, but in Windows, there
is some issues about Skype and Mic Boost... Don't remember, see it in 
Skype web site...) and for last, choose the i-mic (internal microphone)...

Try the sound recorder...

Try Skype...
If Skype worked, please tell me how!

I saw something about alsa drivers too... but I think that Karmic comes with this...

---

### Post by TheTilde on 2009-11-17
Hi
Sound in 9.10 worked for me (audacity, gnome-sound-recorder) first time without any fuss, second time with messing up with alsamixer and some reboots. 
So I think it can work, but maybe pulse is quite unstable.

Perhaps switching to alsa in gstreamer-properties may help?

---

### Post by defaria on 2009-11-22
I can't seem to get the mic working no matter what I do. I have a HP A6750F with a ATI SBx00 Azalia (Intel HDA) sound card. The mic works - I hear it loud and clear out the speakers. The problem is it doesn't register at all in Sound Preferences: Input: Input level nor can I record my voice with the Sound Recorder. And, of course, Skype doesn't work either. Mute is not on, the volume is up but the meter is not registering anything.

HELP!

```

hwinfo --sound
20: PCI 14.2: 0403 Audio device                                 
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_1002_4383
  Unique ID: 5Dex.0MxW5rcNjXE
  SysFS ID: /devices/pci0000:00/0000:00:14.2
  SysFS BusID: 0000:00:14.2
  Hardware Class: sound
  Model: "ATI SBx00 Azalia (Intel HDA)"
  Vendor: pci 0x1002 "ATI Technologies Inc"
  Device: pci 0x4383 "SBx00 Azalia (Intel HDA)"
  SubVendor: pci 0x103c "Hewlett-Packard Company"
  SubDevice: pci 0x2a7f 
  Driver: "HDA Intel"
  Driver Modules: "snd_hda_intel"
  Memory Range: 0xfe024000-0xfe027fff (rw,non-prefetchable)
  IRQ: 16 (193425748 events)
  Module Alias: "pci:v00001002d00004383sv0000103Csd00002A7Fbc04sc03i00"
  Driver Info #0:
    Driver Status: snd_hda_intel is active
    Driver Activation Cmd: "modprobe snd_hda_intel"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

```

---

