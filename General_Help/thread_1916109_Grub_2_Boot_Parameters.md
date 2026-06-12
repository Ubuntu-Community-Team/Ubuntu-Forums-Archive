---
title: "Grub 2 Boot Parameters"
date: 2012-01-27
forum: General Help
---

### Post by SpeedCrazy on 2012-01-27
Hey all,
This is my first post to this forum so please bare with me if i mess something up.
I just finished my first instal of ubuntu server 11.10 successfully:D. 
But my grub setup is kinda screwed up.
When i boot up normally i end up with a screen full of garbled black text on a white background. With some help on another site i discovered that adding console=ttyl to the boot parameters fixed the problem.
Now in order to make this a permanent fix i was instructed to add the following line to my /etc/default/grub:
GRUB_CMDLINE_LINUX_DEFAULT="console=tty1"
When i proceeded to do this and run update-grub this line was created in the boot params:
linux /vmlunz-3.0.0-12-generic-pae root=/dev/mapper/dev-root ro console=ttyl  vt.handoff=7
This line does not allow me to boot, in order to boot i must change that to read
linux /vmlunz-3.0.0-12-generic-pae root=/dev/mapper/dev-root rovt.handoff=7
and add console=ttyl on a separate line.
How would i go about doing this?
Thanks so much,
Speed

---

### Post by hhh on 2012-01-27
GRUB_CMDLINE_LINUX_DEFAULT should have already been in /etc/default/grub at the top of the file. For example mine looks like this (Debian, so it's different than yours)...```
GRUB_DEFAULT=0
GRUB_TIMEOUT=5
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
**GRUB_CMDLINE_LINUX_DEFAULT="quiet"**
GRUB_CMDLINE_LINUX=""
```So I would change my line like so...```
GRUB_CMDLINE_LINUX_DEFAULT="quiet console=tty1"
```Make sure you don't have 2 lines. The other thing, you posted that your boot parameter shows...```
linux /vmlunz-3.0.0-12-generic-pae root=/dev/mapper/dev-root ro console=ttyl vt.handoff=7
```That says ttyl, not tty1. Check /etc/default/grub for typos, then run sudo update-grub again.

---

### Post by SpeedCrazy on 2012-01-27
> **hhh said:**
> GRUB_CMDLINE_LINUX_DEFAULT should have already been in /etc/default/grub at the top of the file. For example mine looks like this (Debian, so it's different than yours)...```
GRUB_DEFAULT=0
GRUB_TIMEOUT=5
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
**GRUB_CMDLINE_LINUX_DEFAULT="quiet"**
GRUB_CMDLINE_LINUX=""
```So I would change my line like so...```
GRUB_CMDLINE_LINUX_DEFAULT="quiet console=tty1"
```Make sure you don't have 2 lines. The other thing, you posted that your boot parameter shows...```
linux /vmlunz-3.0.0-12-generic-pae root=/dev/mapper/dev-root ro console=ttyl vt.handoff=7
```That says ttyl, not tty1. Check /etc/default/grub for typos, then run sudo update-grub again.
It is supposed to say ttyl. It works when added in grub manually.
The line was already their it just had no value. 
The problem is that the line i posted that you quoted has my input is placed inside another parameter that
"ro console=ttyl vt.handoff=7" should read "rovt.handoff=7 console=ttyl" accept that even when corrected to that in grub it does not boot.

---

### Post by hhh on 2012-01-27
> **SpeedCrazy said:**
> It is supposed to say ttyl.

Then why did you add the following, as you said you did?...

GRUB_CMDLINE_LINUX_DEFAULT="console=tty1"

[https://help.ubuntu.com/community/SerialConsoleHowto](https://help.ubuntu.com/community/SerialConsoleHowto)

---

### Post by SpeedCrazy on 2012-01-28
> **hhh said:**
> Then why did you add the following, as you said you did?...

GRUB_CMDLINE_LINUX_DEFAULT="console=tty1"

[https://help.ubuntu.com/community/SerialConsoleHowto](https://help.ubuntu.com/community/SerialConsoleHowto)
It was a typo.
tty1 does not work. It has to be ttyl.

That guide is for grub1, i am using grub 2.

---

