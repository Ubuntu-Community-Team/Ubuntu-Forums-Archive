---
title: "Lucid suspend problem - Thinkpad T22 - immediate resume"
date: 2010-06-24
forum: General Help
---

### Post by AleksBozovic on 2010-06-24
Hi there,

I've been having this problem with Lucid. It did not happen with Karmic or earlier versions. When I hit suspend (any form, lid-close, Fn-F4, or shutdown-sus pend menu), the laptop immediately resumes and shows me the password screen. This happens about 98% of the time. Every one in a while, it lets me suspend, such as when I first try it after an install - tried installing 3 times. Hibernate works fine and resumes properly. Even this erratic resume resumes properly, but never lets my laptop actually suspend.

I'm running the latest (I tried a clean install and an upgrade from Karmic to Lucid). The machine is a Thinkpad T22, P3, 900mhz with a savage gfx card. Not sure which logs I need to post, so I appreciate any help I can get. Right off the bat, here's my "free -m".

```
                 total       used       free     shared    buffers     cached
Mem:              497        464         32          0         27        225
-/+ buffers/cache:          211        285
Swap:             1223          1       1222
```

I would like this to work, I like lucid quite a bit more than karmic, so I'm willing to spend some time on this problem, with some good help.

Thanks

---

### Post by AleksBozovic on 2010-06-24
Ok, I've discovered something new. It only allows me to suspend after a reboot. Every suspend after that resumes immediately. I have tried to edit "00sleep_module" file to change the modes to tuxonice or uswsusp with no results, same thing happens.

Here's my latest sleep log. Not that immediately after suspend it says "awake".

Thu Jun 24 20:08:35 EDT 2010: performing suspend
Thu Jun 24 20:08:43 EDT 2010: Awake.
Thu Jun 24 20:08:43 EDT 2010: Running hooks for resume
/etc/pm/sleep.d/action_wpa resume suspend:success.
/usr/lib/pm-utils/sleep.d/99video resume suspend:success.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:success.
/usr/lib/pm-utils/sleep.d/95led resume suspend:success.
/usr/lib/pm-utils/sleep.d/95anacron resume suspend:success.
/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:success.
/usr/lib/pm-utils/sleep.d/90clock resume suspend:not applicable.
/usr/lib/pm-utils/sleep.d/75modules resume suspend:success.
/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
success.
/usr/lib/pm-utils/sleep.d/49bluetooth resume suspend:not applicable.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:success.
/etc/pm/sleep.d/10_grub-common resume suspend:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:
success.
/usr/lib/pm-utils/sleep.d/00powersave resume suspend:success.
/usr/lib/pm-utils/sleep.d/00logging resume suspend:success.
/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:success.
Thu Jun 24 20:08:47 EDT 2010: Finished.

---

### Post by AleksBozovic on 2010-06-24
Ok, then, let's hear more from the noob who might just figure something out.

This is what I've done (by reading other forums and posts): I've figured out that it's possible the lid that's making the computer wake up, because at the last successful suspend, the laptop woke up when I opened the lid... Hmmmm, unusual. That never happened before. So, I started researching wakeup modes. So, what I ended up doing was:
```
sudo sh -c "echo LID > /proc/acpi/wakeup"
```But what that did was:
```
Device  S-state   Status   Sysfs node
LID       S3    *disabled
SLPB      S3    *disabled
PCI0      S4     disabled  no-bus:pci0000:00
USB       S1     disabled  pci:0000:00:07.2
UART      S3     disabled  pnp:00:0b
```Hmm hmm hmmm. Now, the thing suspends like a charm, but I can only wake it up using the power button. Pressing "Fn" doesn't do the trick anymore. So, now the question (assuming this was a solution) is:

How do I reinstate the Fn button as a wakeup, but keep the lid disabled.

Allright. Now I wait for a responose :p
There's gotta be someone out there.

---

### Post by AleksBozovic on 2010-06-26
I've figured it out, barring any other questions, which I reserve to pose at a later date.

edit /etc/rc.local and add the line
```

sudo sh -c 'echo "LID" > /proc/acpi/wakeup' 
```So, I hope that's it. If not, I'll be back bitching and moaning later on,

---

### Post by AleksBozovic on 2011-09-29
I know I'm answering a year too late (I'm surprised I never got a single email notification for replies). So far, this command works on Ubuntu 10.x, 11.x and Crunchbang (not sure which version).

---

