---
title: "Question on disabling services."
date: 2009-12-10
forum: General Help
---

### Post by Rytron on 2009-12-10
Hi.
I have disabled these services in Boot-Up Manager & Simple Service Manager.

[B][COLOR="red"]acpid-support (keep on for laptops)
apache2
bluetooth
cups
dansguardian
jackd
laptop-mode (keep on for laptops)
lirc
samba
timidity
winbind[/COLOR][/B]

Is it safe to disable the above for my Desktop PC? Also are there more services that I can safely disable?

---

### Post by apreiml on 2009-12-10
Is there any need to disable these services? Please correct me if i'm wrong but as far as i know the services are now started and stopped by events (see upstart). So they are only started if they will be needed.

---

### Post by Rytron on 2009-12-10
Hi apreiml.
Is upstart new as of from Ubuntu 9.10? This must be why the Services option was removed from System -> Administration.

---

### Post by sisco311 on 2009-12-10
> **Rytron said:**
> Hi apreiml.
Is upstart new as of from Ubuntu 9.10? This must be why the Services option was removed from System -> Administration.

*Upstart was first included in Ubuntu in the 6.10 (Edgy Eft) release in late 2006, replacing sysvinit. While the new Upstart daemon is used, most of the services are managed using the old sysvinit scripts. The reason for this has been attributed to missing features that prevent the complete replacement of the existing scripts with native Upstart service descriptions. Since then, Ubuntu 9.10 (Karmic Koala) introduced native Upstart bootup as of Alpha 6.*

[http://en.wikipedia.org/wiki/Upstart]("http://en.wikipedia.org/wiki/Upstart")

The Services option was removed because services-admin is not compatible with the Upstart jobs.

Some of the services are still managed by SysV style init scripts. You can use BUM to disable this services, but you have to manually disable the ones managed by the new Upstart jobs.

Jobs are defined in files placed in /etc/init, the name of the job is the filename under this directory without the .conf extension.

Simply changing the .conf extension of a file will disable the service. i.e.:
```
mv /etc/init/gdm.conf /etc/init/gdm.conf.noexec
``` 
will disable gdm.

Another method to disable a job is to edit the .conf file.

For example, to disable gdm you can edit the file to something like this:
```
description     "GNOME Display Manager"
author          "William Jon McCann <mccann@jhu.edu>"

start on (**never**
          and filesystem
          and started hal
          and tty-device-added KERNEL=tty7
          and (graphics-device-added or stopped udevtrigger))
stop on runlevel [016]
...

```
  

filesystem, started hal,  tty-device-added KERNEL=tty7, graphics-device-added and stopped udevtrigger are events.

By default gdm is started when the filesystem is mounted and the hal daemon is running and so on...

If you add another event (i.e. **never**) to the list gdm will not be started until that event is emitted.

[http://upstart.ubuntu.com/getting-started.html]("http://upstart.ubuntu.com/getting-started.html")

[http://upstart.ubuntu.com/wiki/]("http://upstart.ubuntu.com/wiki/")

---

### Post by Rytron on 2009-12-10
Thank you sisco311. Thats an impressive post.

---

