---
title: "xorg freezes"
date: 2006-05-31
forum: General Help
---

### Post by dmizer on 2006-05-31
something is causing xorg to freeze on me.  i can use programs that are already open, but menus don't work, and i am unable to type.  my mouse works fine, and i can highlight text and close open programs etc.  i can also start new tasks if i have a launcher on my desktop.

the kicker is, that i can ssh into my machine while it is in this state and perform any functions i might so desire.

machine specs are as follows:
NEC versapro va90j 1ghz pIII with 256m of ram and a 60gig hdd.
it has an ati rage mobility P/M video driver and an intel 82440MX chipset

in an attempt to solve this problem i have done the following:
updated to the 686 kernel
reconfigured my sound per [this]("http://easylinux.info/wiki/Ubuntu#How_to_configure_sound_to_work_properly_in_GNOME") page.
completely turned sound off.
removed all desktop tweaks and run in the default theme.
ran a complete memory check via grub (which showed no errors)

i really have no idea what to try next. i don't see any errors in dmesg when this is happening.

anyone with any ideas of what i can look at to try to resolve this?

---

### Post by dmizer on 2006-06-01
couple more things i've done.

upgraded to gaim2.0 beta3
upgraded to firefox 1.5.0.3

it has calmed down significantly after those two updates, but it still happens at least once an hour.

i've also noticed, that using any kind of transparency at all will crash xorg very quickly.

something is very wrong here.

---

### Post by dmizer on 2006-06-02
i worked all day today without a single lockup.

i installed kubuntu desktop and used it all day instead of gnome.  that's the only change i made.  what could be causing gnome to lock like this?  i'd like to keep gnome primarily because i've learned how to tweak it fairly quickly, and also because kde is just too slow on my box.

---

### Post by dmizer on 2006-06-05
maybe it's hardware related?  i had kde lock up on me a couple times yesterday.  last time it locked up so hard i had no keyboard and no mouse at all.  nothing.

i really need some help with this.

gnome only lasts about 20 minutes before it becomes useless.  kde lasts significantly longer but has the same problem.

---

### Post by dmizer on 2006-06-05
[QUOTE=dmizer]maybe it's hardware related?[/QUOTE]
actually ... since i can ssh into my machine, that would leave only two things right?  display adapter or sound card?

my display adapter is a ati rage mobility P/M, and xorg has the following:
```
Section "Device"
        Identifier      "ATI Technologies, Inc. Rage Mobility P/M"
        Driver          "ati"
        BusID           "PCI:0:5:0"
        Option          "UseFBDev"              "true"
EndSection
```

per lspci, i have the Intel Corp. 82440MX AC'97 Audio Controller, and lsmod shows the following for sound:
```
snd_intel8x0           33248  1
snd_ac97_codec         83932  1 snd_intel8x0
snd_pcm_oss            52704  0
snd_mixer_oss          19296  1 snd_pcm_oss
snd_pcm                88840  4 snd_usb_audio,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              24164  1 snd_pcm
snd                    54884  14 snd_usb_audio,snd_rawmidi,snd_seq_device,snd_hwdep,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9600  1 snd
snd_page_alloc         10600  2 snd_intel8x0,snd_pcm
```
note: i do have a usb phone connected to my computer.  but it doesn't seem to matter if it is connected or not.  the problem still happens.

what other hardware or software could be causing this to freeze?

---

### Post by dmizer on 2006-06-05
i'm going to try icewm because when kde freezes, the only way i can get my computer back is to hard reboot.

there has got to be a solution for this.  anyone?

---

### Post by dmizer on 2006-06-06
ahh ... bump!

---

### Post by praxis22 on 2006-07-02
[QUOTE=dmizer]ahh ... bump![/QUOTE]

Strangely enough X used to hang when I using the liveCD, every time I ran it, at some point, (usually when opening a panel of some kind) it would just hang. No way out of it, but a hard reboot. I asumed this was down to the fact that it was trying to load data from the USB CD-ROM, but I don't really know.

It's been stable for the few days I've had the  6.0.6 release installed. try upgrading to that.

Did anything bad happen when you removed sound from the kernel. I think my sound chip (same sound & video as yours) has failed. Never worked under Windows either, so I was thinking of removing sound outright.

later
jb

---

### Post by dmizer on 2006-07-02
never could solve this problem, so i installed fedoracore5 which seems to have solved all my locking problems.  faster too.

i couldn't get sound to work in windows either, needed some kind of proprietary driver from the manufacture.  i wouldn't give up on sound yet.

all i did to "remove" sound from the kernel was just to blacklist all the modules used for sound.

---

