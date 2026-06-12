---
title: "No sound and no sound icon in system settings"
date: 2011-09-16
forum: General Help
---

### Post by anbaldinger on 2011-09-16
Hello,

I have a samsung R580 Hawk and use Ubuntu 11.04 64bit.

I tried to get my microphone jack to work yesterday (no input device showed up in sound preferences) but managed to kill my whole audio and soundcard instead (as it seems).

The problem now is:
- no sound at all
- no gnome-volume-control in the desktop-panel
- no icon "sound" in system settings
- no output devices available in pulse audio volume control
- "$ alsamixer -c 0" shows "invalid card index: 0"
- "$ dmseg | grep snd" and "$ dmesg | grep audio" doesnt show anything.
- "$ lspci | grep -i audio" shows:
```
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
02:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
```

I tried several things I found in help-sites and forums but nothing worked so far.
for example:
- recompile and reinstall pulseaudio
- reinstall Tools for Samsung netbooks
- reinstall kernel
- install latest version of ALSA [https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")

The problem is I dont know what I actually did to end up as miserable as this.

Another problem in solving this is, that I dont really understand how audio-support works in linux with snd_hda_intel, pulseaudio, oss and ALSA. How are they working together?

I hope someone has experienced a problem like that before or knows about audio in linux and can help me.

Thanks for the effort in advance.

Greets, Andrew

[EDIT] Thread should be moved to General Help I think. It was a mistake to post it in "Installation & Upgrades". But I think users cant move an own thread themselves.

---

### Post by anbaldinger on 2011-09-17
No idea anyone? Does nobody know enough about the linux audio system?
I know doubleposts are not welcome, but I dont know how to get my post up otherwise.

I tried to install the latest ALSA system (drivers, lib and util) but when I try "$ sudo alsaconf" after reboot I get "No supported PnP or PCI card found".
Maybe this is a point to start solving the problem.

I've read, that ALSA cannot find the soundcard, if another process is accessing it. Is that right? And how do I find out which process is accessing the soundcard?

---

### Post by rockophonic on 2011-09-17
I've personally experienced loss of sound from pulse audio on serveral ubuntu builds, I believe since about version 9 or so.  

While I couldn't answer exactly why this bug occurs, I can tell you that in my situation, deleting the .pulse directory from my home directory and then rebooting brought the sound back on my system.

---

### Post by nothingspecial on 2011-09-18
> **anbaldinger said:**
> 

[EDIT] Thread should be moved to General Help I think. It was a mistake to post it in "Installation & Upgrades". But I think users cant move an own thread themselves.

Done :)

---

### Post by anbaldinger on 2011-09-18
Thanks for moving.

Deleting .pulse didn't help.

I put the problem now down to this:

$ lspci -v | less:
```
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
        Subsystem: Samsung Electronics Co Ltd Device c06a
        Flags: bus master, fast devsel, latency 0, IRQ 7
        Memory at f0b00000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel modules: snd-hda-intel

```

$ sudo aplay -l:
```
aplay: device_list:240: no soundcards found...
```

$ lspci -n | grep 00:1b.0:
```
00:1b.0 0403: 8086:3b56 (rev 06)
```

From [here]("http://cateee.net/lkddb/web-lkddb/SND_HDA_INTEL.html") I know, that I need the module snd_hda_intel.

So I reinstalled the alsa packages (drivers, lib, utila and framework) with [this helpsite]("https://help.ubuntu.com/community/HdaIntelSoundHowto").
But then after reboot, when I try "$ sudo alsaconf" it always replies "No supported PnP or PCI card found".

$ wget -O alsa-info.sh [http://alsa-project.org/alsa-info.sh](http://alsa-project.org/alsa-info.sh) && bash ./alsa-info.sh:
```
!!ALSA Version
!!------------

Driver version:     
Library version:    1.0.24.1
Utilities version:  1.0.24.2
```

So no driver.

When I try "$ sudo modprobe snd-" and the double-press TAB it shows snd-hda-intel as module.
But when I try "$ sudo modprobe snd-hda-intel" it shows:
```
FATAL: Error inserting snd (/lib/modules/2.6.38-11-generic/kernel/sound/acore/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
WARNING: Error inserting snd_pcm (/lib/modules/2.6.38-11-generic/kernel/sound/acore/snd-pcm.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_hwdep (/lib/modules/2.6.38-11-generic/kernel/sound/acore/snd-hwdep.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_hda_codec (/lib/modules/2.6.38-11-generic/kernel/sound/pci/hda/snd-hda-codec.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.38-11-generic/kernel/sound/pci/hda/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```

And dmesg gives:
```
[ 1281.021557] snd: Unknown symbol unregister_sound_special (err 0)
[ 1281.022816] snd: Unknown symbol register_sound_special_device (err 0)
[ 1281.025541] snd_timer: Unknown symbol snd_info_register (err 0)
[ 1281.025709] snd_timer: Unknown symbol snd_info_create_module_entry (err 0)
[ 1281.025919] snd_timer: Unknown symbol snd_info_free_entry (err 0)
[ 1281.026308] snd_timer: Unknown symbol __snd_printk (err 0)
[ 1281.026474] snd_timer: Unknown symbol snd_iprintf (err 0)
[ 1281.026710] snd_timer: Unknown symbol snd_ecards_limit (err 0)
[ 1281.026970] snd_timer: Unknown symbol snd_oss_info_register (err 0)
[ 1281.027158] snd_timer: Unknown symbol snd_unregister_device (err 0)
[ 1281.027368] snd_timer: Unknown symbol snd_device_new (err 0)
[ 1281.027738] snd_timer: Unknown symbol snd_register_device_for_dev (err 0)

```

Can anyone help me with that?
Why is snd an unknown symbol and why can't I load the module snd-hda-tinel?

---

