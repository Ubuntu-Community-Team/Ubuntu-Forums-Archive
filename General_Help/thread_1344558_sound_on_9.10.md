---
title: "sound on 9.10"
date: 2009-12-03
forum: General Help
---

### Post by abqhandyman on 2009-12-03
Because ubuntu recommended an upgrade to 9.10, I did so, but now do not have sound.

This seems to be a very common problem with this distribution.  One of my favorite things is to listen to the music player on random tracks.  Had I had it installed last night while my girlfriend was visiting, she might have been distracted into sleep, but not so.

My computer is all I have to listen to in my room, so this is no trifling matter.   I've tried a couple things, but none has worked so far.

Thank you for your comment,

---

### Post by b0b138 on 2009-12-03
Need more input (name that movie)

What sound card you got?

What is the output of lspci?

---

### Post by Zoot7 on 2009-12-03
Can you post the output of
```
aplay -l
```

---

### Post by abqhandyman on 2009-12-03
Thanks both for replies.

dan@dan-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CK8S [NVidia CK8S], device 0: Intel ICH [NVidia CK8S]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CK8S [NVidia CK8S], device 2: Intel ICH - IEC958 [NVidia CK8S - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
dan@dan-desktop:~$ lspci
00:00.0 Host bridge: nVidia Corporation nForce3 250Gb Host Bridge (rev a1)
00:01.0 ISA bridge: nVidia Corporation nForce3 250Gb LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation nForce 250Gb PCI System Management (rev a1)
00:02.0 USB Controller: nVidia Corporation CK8S USB Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation CK8S USB Controller (rev a1)
00:02.2 USB Controller: nVidia Corporation nForce3 EHCI USB 2.0 Controller (rev a2)
00:06.0 Multimedia audio controller: nVidia Corporation nForce3 250Gb AC'97 Audio Controller (rev a1)
00:08.0 IDE interface: nVidia Corporation CK8S Parallel ATA Controller (v2.5) (rev a2)
00:0a.0 IDE interface: nVidia Corporation nForce3 Serial ATA Controller (rev a2)
00:0b.0 PCI bridge: nVidia Corporation nForce3 250Gb AGP Host to PCI Bridge (rev a2)
00:0e.0 PCI bridge: nVidia Corporation nForce3 250Gb PCI-to-PCI Bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)
01:00.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (Secondary) (rev 01)
02:09.0 Modem: Motorola SM56 Data Fax Modem (rev 04)
02:0d.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
dan@dan-desktop:~$ 

Cheers.

---

### Post by Zoot7 on 2009-12-04
Well Alsa sees your sound card okay so there *should* be sound. Chances are Pulseaudio is the problem. This thread here might be of use to you:
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

Failing that, you could try removing Pulseaudio (you're better off you stick with it though if at all possible).
```
sudo apt-get remove pulseaudio
```

---

### Post by ellgor on 2009-12-04
Hi,

Had the same when I upgraded, for me it was, right click on the sound icon in the top panel, for some reason all the mute boxes were set to off, obviously un-mute them, hope this of use.

Regards, Ellgor

---

### Post by ellgor on 2009-12-04
Hi,

Had the same when I upgraded, for me it was, right click on the sound icon in the top panel, for some reason all the mute boxes were set to off, obviously un-mute them, hope this of use.

Regards, Ellgor

---

### Post by ellgor on 2009-12-04
Hi,

Had the same when I upgraded, for me it was, right click on the sound icon in the top panel, for some reason all the mute boxes were set to off, obviously un-mute them, hope this of use.

Regards, Ellgor

---

### Post by abqhandyman on 2009-12-04
Ellgor:  I LOVE YOU, MAN!

[solved]

The icon is in the top right corner.

---

### Post by Zoot7 on 2009-12-04
Ah so it was muted by default! Truth be told the same thing happened to me with both Installs of Karmic.

---

### Post by abqhandyman on 2009-12-04
You can also see that in system>preferences>sound.

---

