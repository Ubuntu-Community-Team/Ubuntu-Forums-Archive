---
title: "Ubuntu 11.04 black screen after wakeup on a dual monitor configuration"
date: 2011-08-25
forum: General Help
---

### Post by relgames on 2011-08-25
(not sure where to post this thread)

Updated from 10.04 to 11.04 couple of weeks ago on my Dell Optiplex GX620 (graphics ATI Technologies Inc RV380 [Radeon X600 (PCIE)]) with 2 monitors.

I usually put my machine to a standby mode so I can just resume it next day and continue current task, but after upgrade it resumes to a black screen. When I press CTRL+ALT+F1 it shows console but just on first monitor only (normally it shows the same console on both monitors). If I restart GDM is starts just on first monitor.

dmesg contains suspicions entry:
> 
[24925.949191] PM: resume of drv:sd dev:2:0:0:0 complete after 6727.948 msecs
[24925.949208] PM: resume of drv:scsi_device dev:2:0:0:0 complete after 6727.916 msecs
[24925.949221] PM: resume of drv:scsi_disk dev:2:0:0:0 complete after 6690.254 msecs
[24925.949324] PM: resume of devices complete after 6729.474 msecs
[24925.949521] PM: resume devices took 6.732 seconds
[24925.949699] PM: Finishing wakeup.
[24925.949701] Restarting tasks ... done.
[COLOR=Red][24925.984137] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id[/COLOR]
X.org log doesn't seem to contain any errors.

It's really annoying and I lose a lot time every day because I need to (re)start my machine and start all programs I use.

```
$ uname -r
2.6.38-11-generic
```dmesg [http://pastebin.com/PU3jLmx8](http://pastebin.com/PU3jLmx8)
X.org log [http://pastebin.com/FPRUkKn8](http://pastebin.com/FPRUkKn8)
lshw [http://pastebin.com/8vzvEF9p](http://pastebin.com/8vzvEF9p)

---

### Post by relgames on 2011-08-26
anybody?

---

### Post by relgames on 2011-09-01
I'va created a bug: [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/837212](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/837212)

---

### Post by roarkethemerc on 2011-09-05
> **relgames said:**
> (not sure where to post this thread)

Updated from 10.04 to 11.04 couple of weeks ago on my Dell Optiplex GX620 (graphics ATI Technologies Inc RV380 [Radeon X600 (PCIE)]) with 2 monitors.

I usually put my machine to a standby mode so I can just resume it next day and continue current task, but after upgrade it resumes to a black screen. When I press CTRL+ALT+F1 it shows console but just on first monitor only (normally it shows the same console on both monitors). If I restart GDM is starts just on first monitor.

dmesg contains suspicions entry:
X.org log doesn't seem to contain any errors.

It's really annoying and I lose a lot time every day because I need to (re)start my machine and start all programs I use.

```
$ uname -r
2.6.38-11-generic
```dmesg [http://pastebin.com/PU3jLmx8](http://pastebin.com/PU3jLmx8)
X.org log [http://pastebin.com/FPRUkKn8](http://pastebin.com/FPRUkKn8)
lshw [http://pastebin.com/8vzvEF9p](http://pastebin.com/8vzvEF9p)



You tried to disable (from your graphic card panel) the primary used monitor and to use the one you want ? If you want this, of course.

---

### Post by relgames on 2011-09-14
> **roarkethemerc said:**
> You tried to disable (from your graphic card panel) the primary used monitor and to use the one you want ? If you want this, of course.
If I have 2 monitors I want to use them both. So disabling 1 monitor is not a solution.

---

### Post by relgames on 2011-09-15
Just tried kernel v3.1-rc4-oneiric ([http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.1-rc4-oneiric/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.1-rc4-oneiric/)) and the issue is fixed.

Continuing with kernel 3.

---

