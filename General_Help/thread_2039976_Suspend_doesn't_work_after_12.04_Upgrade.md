---
title: "Suspend doesn't work after 12.04 Upgrade"
date: 2012-08-10
forum: General Help
---

### Post by beenny on 2012-08-10
Hello All,

I recently upgraded my laptop to 12.04. I've noticed that suspend doesn't work. This is the case when I shut the lid or try to do it manually. All that happens is that the wifi disconnects for a second or two (as if it is going to suspend) and then it reconnects and all is back to normal. This is also the case when I try to hibernate manually.

I was wondering if anyone has any thoughts. I have a lenov0 x220 with an SSD and kernel 3.2.0-27

Thanks,

bg

---

### Post by 2F4U on 2012-08-10
What are the hardware specs? Did you look into /var/log/pm-suspend.log? My guess would be that a hardware component (maybe WiFi) prevents the machine from suspending.

---

### Post by beenny on 2012-08-10
I'm not sure exactly what I'm looking for in this but there seem to be some fails in the network manager:

Thu Aug  9 22:23:33 PDT 2012: Inhibit found, will not perform suspend
Thu Aug  9 22:23:33 PDT 2012: Running hooks for resume
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:

/usr/lib/pm-utils/sleep.d/99video resume suspend: disabled.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:

/usr/lib/pm-utils/sleep.d/95led resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:

/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:

/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:

/etc/pm/sleep.d/10_grub-common resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.

---

### Post by beenny on 2012-08-11
I also wanted to note that this doesn't appear to be a problem with my desktop running 12.04.

Anyone have any thoughts on how to prevent the wifi from interferring with sleep?

Thanks,

gb

---

### Post by beenny on 2012-08-12
From looking around I think I may need to blacklist something but I'm not quite sure what that would be or how I would do that...Any thoughts would be appreciated...

thanks,

bg

---

### Post by beenny on 2012-08-13
I hate to bump but I'd really appreciate some thoughts on this...Not being able to suspend is a pretty big nuisance for a travel laptop...

Thanks,

bg

---

