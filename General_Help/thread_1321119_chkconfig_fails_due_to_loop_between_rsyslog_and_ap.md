---
title: "chkconfig fails due to loop between rsyslog and apache2"
date: 2009-11-09
forum: General Help
---

### Post by hymerman on 2009-11-09
I've just installed 9.10, and have barely installed any packages so far (git and gitosis, mdadm, that's about it). I'm just trying to install Pulse continuous integration server, which involves putting a link to a startup script in /etc/init.d and running chkconfig as per the instructions here:

[http://confluence.zutubi.com/display/pulse0200/Running+as+a+Service](http://confluence.zutubi.com/display/pulse0200/Running+as+a+Service)

But when I do that, I get this output:
```

ben@jack:~$ sudo chkconfig --add pulse
insserv: warning: script 'pulse' missing LSB tags and overrides
insserv: warning: script 'udev-finish' missing LSB tags and overrides
insserv: warning: script 'udevtrigger' missing LSB tags and overrides
insserv: warning: script 'hwclock' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (0 6) of script `sendsigs' overwrites defaults (empty).
insserv: warning: current start runlevel(s) (6) of script `reboot' overwrites defaults (empty).
insserv: warning: script 'rsyslog' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (0 6) of script `wpa-ifupdown' overwrites defaults (empty).
insserv: warning: script 'module-init-tools' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (0 6) of script `umountroot' overwrites defaults (empty).
insserv: warning: script 'atd' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (0 6) of script `umountfs' overwrites defaults (empty).
insserv: warning: script 'hwclock-save' missing LSB tags and overrides
insserv: warning: script 'rsyslog-kmsg' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (0) of script `halt' overwrites defaults (empty).
insserv: warning: script 'cron' missing LSB tags and overrides
insserv: warning: script 'procps' missing LSB tags and overrides
insserv: warning: script 'ufw' missing LSB tags and overrides
insserv: warning: script 'dmesg' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (0 6) of script `networking' overwrites defaults (empty).
insserv: warning: script 'udev' missing LSB tags and overrides
insserv: warning: script 'apport' missing LSB tags and overrides
insserv: warning: script 'udevmonitor' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (0 6) of script `umountnfs.sh' overwrites defaults (empty).
insserv: There is a loop between service rsyslog and apache2 if stopped
insserv:  loop involving service apache2 at depth 3
insserv:  loop involving service rsyslog at depth 2
insserv:  loop involving service udev at depth 1
insserv: There is a loop between service rsyslog and apache2 if stopped
insserv:  loop involving service mysql at depth 2
insserv:  loop involving service hwclock at depth 3
insserv: exiting without changing boot order!
/sbin/insserv failed, exit code 1
pulse                     0:off  1:off  2:off  3:off  4:off  5:off  6:off

```

As I say, there's barely anything I could have done to cause this, this is practically Ubuntu as it was put on the CD. Is this a known problem? I found some bug reports recently but there was nothing conclusive. Is there a workaround?

---

### Post by Giblet5 on 2009-11-09
It's the package that's barfing. Not Ubuntu.

Java applications don't work very well on any platform, even the ones the application's developers developed it on ... and now this one doesn't run on the 10-day-old OS. Well, I am shocked. SHOCKED!

You're going to have to hound the folks on the Zutubi web about this one, but I suspect they'll push you in the direction of an established Linux standard, like Redhat EL or CentOS, with specific patches, running a VERY specific jre version.

In the future, avoid Oracle Java whenever possible.

---

### Post by hymerman on 2009-11-10
I wasn't aware I was running Oracle Java, though I remember having trouble running Pulse on older versions of Ubuntu, where I had to install the Sun jre. Do you think this would fix the problem? Also, why would Ubuntu ship with something that should be "avoided wherever possible"?

---

### Post by jsankey on 2009-11-11
> **Giblet5 said:**
> It's the package that's barfing. Not Ubuntu.

This is incorrect, it is not a problem with Pulse itself.  The original message contains only a warning about missing LSB entries (which are not critical) from the Pulse init script, and for many other standard Ubuntu packages.  The actual error is further down and nothing to do with Pulse.  See:

[http://ubuntuforums.org/showthread.php?t=1321119]("http://ubuntuforums.org/showthread.php?t=1321119")

for more details (the gist is that using chkconfig on Debian-based systems is not recommended).

> **Giblet5 said:**
>  Java applications don't work very well on any platform, even the ones the application's developers developed it on ... and now this one doesn't run on the 10-day-old OS. Well, I am shocked. SHOCKED!

I really don't think this anti-Java rant is called for.

> **Giblet5 said:**
>  You're going to have to hound the folks on the Zutubi web about this one, but I suspect they'll push you in the direction of an established Linux standard, like Redhat EL or CentOS, with specific patches, running a VERY specific jre version.

And I would prefer if you didn't raise unsubstantiated suspicions about how we support our customers.  We place no such  specific restrictions on the platforms we support.

Cheers,
Jason

---

### Post by dekadance on 2010-02-04
uninstall chkconfig : #sudo apt-get remove chkconfig and then try to install again. 
this worked for me; actually isntallation resumed as soon I've uninstalled chkconfig:)
use as sugested here [https://help.ubuntu.com/community/SwitchingToUbuntu/FromLinux](https://help.ubuntu.com/community/SwitchingToUbuntu/FromLinux) or rcconf instead of chkconfig.

take care

---

