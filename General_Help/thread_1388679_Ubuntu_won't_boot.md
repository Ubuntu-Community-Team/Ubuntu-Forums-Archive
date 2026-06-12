---
title: "Ubuntu won't boot"
date: 2010-01-23
forum: General Help
---

### Post by PoopyTheJ on 2010-01-23
I can't get my Ubuntu install to boot. I have win7 and Ubuntu as dual boot, I can boot into win7 fine, but I do all my schoolwork in Ubuntu. I'm running Koala, when Ubuntu boots, I see the white ubuntu logo on a black background for a second or two, then the screen goes black and instead of going further with the progress bar the screen stays black and there is no HDD activity. The computer then stays on the black screen with no HDD activity indefinitely. I don't know how to read the logs from my Ubuntu install without going to administration. If someone can tell me where they are stored I can get them and post the codes here. Please help, I have a two large papers due this weekend and if I can't get into Ubuntu I'm screwed!

---

### Post by PoopyTheJ on 2010-01-23
Ok, found them Syslog shows,

```
Jan 23 12:12:48 poopythej-desktop 
```

Messages shows,

```
Jan 23 12:12:48 poopythej-desktop kernel: imklog 4.2.0, log source = /var/run/rsyslog/kmsg started.
Jan 23 12:12:48 poopythej-desktop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="932" x-info="http://www.rsyslog.com"] (re)start
Jan 23 12:12:48 poopythej-desktop rsyslogd: rsyslogd's groupid changed to 102
Jan 23 12:12:48 poopythej-desktop rsyslogd: rsyslogd's userid changed to 101
Jan 23 12:12:48 poopythej-desktop kernel: [    0.000000] Initializing cgroup subsys cpuset
Jan 23 12:12:48 poopythej-desktop kernel: [    0.000000] Initializing cgroup subsys cpu
Jan 23 12:12:48 poopythej-desktop kernel: [    0.000000] Linux version 2.6.31-17-generic-pae (buildd@palmer) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #54-Ubuntu SMP Thu Dec 10 17:23:29 UTC 2009 (Ubuntu 2.6.31-17.54-generic
```

Kern log shows

```
Jan 23 12:12:48 poopythej-desktop kernel: imklog 4.2.0, log source = /var/run/rsyslog/kmsg started.
Jan 23 12:12:48 poopythej-desktop kernel: [    0.000000] Initializing cgroup subsys cpuset
Jan 23 12:12:48 poopythej-desktop kernel: [    0.000000] Initializing cgroup subsys cpu
Jan 23 12:12:48 poopythej-desktop kernel: [    0.000000] Linux version 2.6.31-17-generic-pae (buildd@palmer) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #54-Ubuntu SMP Thu Dec 10 17:23:29 UTC 2009 (Ubuntu 2.6.31-17.54-generic-pae)
Jan 23 12:12:48 poopythej-desktop kernel: [    0.000000] KERNEL supported cpus:
Jan 23 12:12:48 poopythej-desktop kernel: [    0.000000]   Intel GenuineIntel
Jan 23 12:12:48 poopythej-desktop
```

Auth log shows nothing
Debug shows,

```
Jan 23 12:12:48 poopythej-desktop kernel: [    0.000000] 
```

---

### Post by Bearly Able on 2010-01-23
Hi,

I don't know if this helps, but I had exactly the same problem today when I started up after earlier updates.  I booted using recovery mode and chose "repair broken packages", after which I could reboot and Ubuntu loaded normally.

Unfortunately, it has also re-installed pulseaudio, which I had removed because it was causing problems with my sound, and it now won't allow me to remove it without also removing ubuntu-desktop.

Lesley

---

### Post by PoopyTheJ on 2010-01-23
how do I boot up using recovery mode and choose repair broken packages, is that the recovery kernel choice I see in grub?

As more info I checked the HDD and there were no errors found using e2fsck.

---

### Post by Bearly Able on 2010-01-23
Yes, sorry, my poor choice of words.

---

### Post by PoopyTheJ on 2010-01-23
No I'm still learning this whole Ubuntu/Linux thing I'll give that a try, thanks!

---

### Post by PoopyTheJ on 2010-01-23
You know I also installed updates last night, wonder if there's a broken update floating around?

---

### Post by PoopyTheJ on 2010-01-23
trying to fix broken packages doesn't work, still hangs at the same place.

---

### Post by PoopyTheJ on 2010-01-24
Nobody knows anything huh? Well I've looked online and seemingly everyoen else doesn't know anything either. I've wound up reinstalling Ubuntu for the last time with this, hopefully it gets sorted so this doesn't happen anymore.

---

