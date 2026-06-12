---
title: "ubuntu clock an hour ahead"
date: 2009-08-02
forum: General Help
---

### Post by Tak11 on 2009-08-02
no matter what I set the time-zone to, or if I adjust it manually, its ALWAYS one hour behind my actual time after I reboot, anyone know the problem? 

<3.

---

### Post by lisati on 2009-08-02
It could be related to whether or not your system is set to use "UTC". The exact details of fixing it elude me for the moment, but I have come across this before.

---

### Post by Tak11 on 2009-08-05
> **lisati said:**
> It could be related to whether or not your system is set to use "UTC". The exact details of fixing it elude me for the moment, but I have come across this before.

i tried enableing, and disableing UTC, still no luck =(

---

### Post by razorboy5 on 2009-08-05
just throwing something out there
what's the time set to in BIOS?

---

### Post by slakkie on 2009-08-05
What happens when you set the correct TZ in your shell?

export TZ="Europe/Amsterdam" for example, or "Americas/Aruba".

Maybe run ntpdate, and see what happens.

Also check /etc/timezone

---

### Post by Tak11 on 2009-08-06
> **slakkie said:**
> What happens when you set the correct TZ in your shell?

export TZ="Europe/Amsterdam" for example, or "Americas/Aruba".

Maybe run ntpdate, and see what happens.

Also check /etc/timezone

still no =( though i found out /etc/timezone wasn't updateing properly, i canged it, ran the export line, and when i type

sudo ntpdate ntp.ubuntu.com

it sets me forward an hour >.<

---

### Post by slakkie on 2009-08-06
```

sudo hwclock --show
Thu 06 Aug 2009 11:22:30 AM CEST  -0.375789 seconds

```

See [http://linux.die.net/man/8/hwclock](http://linux.die.net/man/8/hwclock)

---

### Post by Tak11 on 2009-08-07
> **slakkie said:**
> ```

sudo hwclock --show
Thu 06 Aug 2009 11:22:30 AM CEST  -0.375789 seconds

```

See [http://linux.die.net/man/8/hwclock](http://linux.die.net/man/8/hwclock)

i tried

sudo hwclock --set --date "etc..

still didn't work on restart >.<

---

### Post by P4man on 2009-08-07
are you dual booting windows and ubuntu?
Windows uses the BIOS clock as system time, Linux sees the BIOS clock as UTC and adjusts the system time according to timezone/ daylight savings time. If you boot from one to the other, your clock will be messed.

Fortunately, you can change this behaviour in either windows or linux. In windows it depends what version (I believe using UTC is at least partially broken in vista ), but try changing or adding this key:

HKLM\SYSTEM\CurrentControlSet\Control\TimeZoneInformation\RealTimeIsUniversal

set the value to 1

Or if you want to change the behaviour in ubuntu, edit:

/etc/default/rcS

Change:

```
UTC=yes
```

in to:

```
UTC=no
```

reboot.

---

### Post by Tak11 on 2009-08-07
nah I'm not, I upgraded to Jaunty and my clock is fixed, but now my hda-intel audio is broken,.. again *sighs*

---

### Post by P4man on 2009-08-07
Had the same. Try this:
```
alsamixer -c 0
```

Turn PCM volume up again. For some reason it was muted after I upgraded.

---

### Post by Tak11 on 2009-08-07
> **Tak11 said:**
> no matter what I set the time-zone to, or if I adjust it manually, its ALWAYS one hour behind my actual time after I reboot, anyone know the problem? 

<3.

> **P4man said:**
> Had the same. Try this:
```
alsamixer -c 0
```

Turn PCM volume up again. For some reason it was muted after I upgraded.

i had to add 

options snd-hda-intel enable_msi=1
options snd-hda-intel model=3stack enable=yes
options snd-hda-intel model=auto position_fix=1 enable=yes
options snd-hda-intel model=hp-dv5

to /etc/modprobe.d/alsa-base.conf

thanks though <3.

---

