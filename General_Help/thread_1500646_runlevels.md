---
title: "runlevels"
date: 2010-06-03
forum: General Help
---

### Post by lo.j on 2010-06-03
hello everyone.

i'm trying to edit runlevel 2 (the default one?) to boot into text-only mode, still having gdm on runlevel 3.
i have sysv-rc-conf and rcconf installed.

so, my questions:

1) i tryed to disable gdm from runlevel 2 (both manually and with sysv-rc-conf) and /etc/rc2.d/S20gdm became K20gdm, ok.
i then did a reboot but nothing changed, the graphical login was there!
"telinit 2", "telinit 3" and again "telinit 2" also does nothing...

2) i guess i don't fully understand rcconf. it gives you the ability to start/stop services but...
what about runlevels?
does it act only on the default (2?) one?

3) what about /etc/init.d/* and rc-update?
do i have to use them somehow to save my changes?
don't think so...

thanks... :)

---

### Post by lo.j on 2010-06-03
up O:)

---

### Post by lo.j on 2010-06-04
up2 O:)

---

### Post by john newbuntu on 2010-06-04
The newer versions of ubuntu use the upstart mechanism for event based job control instead of the runlevels of systemV init.  rc jobs are run as a part of upstart.  gdm is also triggered by upstart.
To use CLI mode, you would remove the /etc/init/gdm.conf file(create a backup first).  To bring down an existing gdm session, use the command "sudo service gdm stop" from a virtual terminal.

---

### Post by c9-3Rr0r on 2010-06-04
I think that update-rc.d will be helpful

```

sudo update-rc.d gdm stop

```

if I remember correct, to be sure please check the man pages, I don't want be a reason of your mess in computer :)

---

### Post by lo.j on 2010-06-06
ok, i'm trying to understand...

till now i think i learned (but correct me if i'm wrong) that everything we need is in /etc/init direcctory.
/etc/rc?.d are not used anymore (so why are they created?)

any program (now job) configuration file has the runlevel information inside (start on runlevel..., stop on runlevel...). in fact i edited gdm.conf ("stop on runlevel [0126]") and now i can boot the system with no graphical login.

one question:
with "sudo start gdm" i can start gnome and, then, with "sudo gdm stop" or "sudo telinit 2" i can stop gnome but i'm not able to start it with "sudo telinit 3", it says "starting system pulseaudio daemon" and it freeze...
in /etc/init i don't have anything relative to pulseaudio, how can i debug this situation?

thanks!

@c9-3Rr0r
i think that "sudo update-rc.d gdm stop" will search for gdm in /etc/init.d.
it says "update-rc.d: warning: /etc/init.d/gdm missing LSB information"

---

### Post by Leppie on 2010-06-06
if you want to use a system that boots into cli for runlevel 2 and in gui for runlevels 3, 4 and 5, modify the gdm.conf like this:
```
start on (filesystem
          and RUNLEVEL=[345]
          and started dbus
          and (graphics-device-added fb0 PRIMARY_DEVICE_FOR_DISPLAY=1
               or drm-device-added card0 PRIMARY_DEVICE_FOR_DISPLAY=1
               or stopped udevtrigger))
stop on runlevel [0126]
```
like this, you can use telinit to start/stop x

---

### Post by lo.j on 2010-06-06
ok, i added that line but nothing has changed.
(by the way, i guess that "and RUNLEVEL=[345]" and "and runlevel [345]" are equivalent...)

```
$ sudo telinit 3

Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service S20alsa-mixer-save start

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the start(8) utility, e.g. start S20alsa-mixer-save
start: Unknown job: S20alsa-mixer-save

Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service S20gdm start

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the start(8) utility, e.g. start S20gdm
start: Unknown job: S20gdm

 * Starting system PulseAudio Daemon [ OK ]
```

S20alsa-mixer-save and S20gdm, along with many others, are in /etc/rc3.d but i just learned that rc?.d directories are no longer used, runlevels are handled by /etc/init scripts...
so, what's the matter?

thank you, again...

---

### Post by Leppie on 2010-06-06
did you reboot after making the changes?

yes, i believe the two statements have the same result.

---

### Post by lo.j on 2010-06-06
no but i've just done a reboot and nothing's changed...

sorry to bother you further...

---

### Post by Leppie on 2010-06-06
an alternative would be that instead of using runlevel 2 with cli, you use runlevel 3 as the default cli environment.

---

### Post by lo.j on 2010-06-06
well, guess that it should be independent of the runlevel...

i don't understant why, and how, it searches for S20alsa-mixer-save and S20gdm...

---

### Post by Leppie on 2010-06-06
> **lo.j said:**
> well, guess that it should be independent of the runlevel...
normally it should be, but i don't know how runlevel 3 is set up by default.
after disabling gdm with update-rc.d, did you enable it again?

---

### Post by lo.j on 2010-06-06
no, wait... i didn't use update-rc.d!

before i know about upstart i handled rc?.d symlinks by hand.

later i also tried "sudo update-rc.d gdm stop" as suggested but it seems it searches for gdm in /etc/init.d: "update-rc.d: warning: /etc/init.d/gdm missing LSB information"

---

### Post by Leppie on 2010-06-06
so did you remove any symlinks while trying to get rid of gdm in rc2?

have you tried adding gdm to rc.d?
```
sudo update-rc.d gdm start
```

---

### Post by lo.j on 2010-06-06
thanks, tomorrow i'll make some attempts...

one thing i still don't understand... the connection, if exists, between upstart (/etc/init) and rc?.d (/etc/init.d) mechanism....

---

### Post by Leppie on 2010-06-06
upstart needs to maintain some connection with rc.d for compatiblity reasons.
if you want to see which services are controlled by upstart and which by sysv, you could install webmin.

---

### Post by lo.j on 2010-06-07
a,ok.

> upstart needs to maintain *some* connection with rc.d
the logic behind that "*some*" is not so clear, is it?

> if you want to see which services are controlled by upstart and which by sysv, you could install webmin
is webmin the only way?
isn't there a specific tool like sysv-rc-conf or rcconf were for the old sysv mechanism?

---

### Post by john newbuntu on 2010-06-07
Yes, you can use sysv-rc-conf or rcconf  to change the sysV init jobs.  These do not affect upstart.

To list your upstart jobs, use: "sudo initctl list".   You will notice a job called "rc".  That is what kicks off the sysV style scripts in /etc/rcX (typically rc2).

---

### Post by lo.j on 2010-06-07
ok, but the rc job doesn't tell me which daemon/program/script is handled by the old sysv/rc?.d system and which one by the new upstart machanism...

for example i have /etc/init/gdm.conf and /etc/rc3.d/gdm... why? i think those duplictaes could cause some conflict somehow... certainly it makes me confused... :confused:

---

### Post by john newbuntu on 2010-06-07
The "rc" job is a part of upstart mechanism.  It has the config defined in /etc/init/rc.conf , which basically kicks off the sysV init scripts in the corresponding runlevel.

I do not see any /etc/rc*.d/gdm in my install of Karmic or Lucid desktop installs, although there is an /etc/init.d/gdm.  I have not made any changes to these config directories.  So, I am not sure how those got in there in your case or how those got removed in mine.

---

### Post by lo.j on 2010-06-07
it's probably because, before knowing upstart, i configurated rc?.d directories with sysv-rc-conf and rcconf (and by hand)...

though now, i don't know anymore which one has to remain there and which one it needs to be removed...

---

