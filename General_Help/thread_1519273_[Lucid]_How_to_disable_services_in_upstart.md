---
title: "[Lucid] How to disable services in upstart?"
date: 2010-06-27
forum: General Help
---

### Post by digmike on 2010-06-27
Hi,

I recently discovered upstart is launching sshd on my machine even though I disabled it with `sudo update-rc.d -f ssh remove`. I tried to find a way to prevent upstart from launching ssh by default, but the best I can think of is removing /etc/init/ssh.conf (I just uninstalled openssh-server).

I'd like to disable it without doing this, though. This would make it easier to enable sshd when I need it.

Anyone know what the best practice for this is?

Thanks!

---

### Post by gadolinio on 2010-06-28
Mmmm how about pressing alt+F2 and then running gnome-session-properties?
It has a list of apps run when starting a session...

---

### Post by digmike on 2010-06-28
> **gadolinio said:**
> Mmmm how about pressing alt+F2 and then running gnome-session-properties?
It has a list of apps run when starting a session...

As you say, those are apps launched in my session. sshd is not there; it's launched when the machine comes up, before any session is even started.

---

### Post by dino99 on 2010-06-28
general help

[https://help.ubuntu.com/community/InternetAndNetworking](https://help.ubuntu.com/community/InternetAndNetworking)

---

### Post by digmike on 2010-06-28
> **dino99 said:**
> general help

[https://help.ubuntu.com/community/InternetAndNetworking](https://help.ubuntu.com/community/InternetAndNetworking)

Thanks for the link. I couldn't find anything relevant to upstart/sshd though. Could you point it out please?

---

### Post by BugBuster on 2010-06-28
I have always done this using the following method and it works. But I am not 100% sure this is the best way to do so.

```

$cd /etc/init

```

Then rename the .conf file of the service that you want to disable to something else. I do it like this.

```

$sudo mv sshd.conf sshd.conf.off

```

Now reboot and check using the following command;

```

sudo netstat -ltunp

```

sshd should not be listed in there.

---

### Post by digmike on 2010-06-28
> **BugBuster said:**
> I have always done this using the following method and it works. But I am not 100% sure this is the best way to do so.

```

$cd /etc/init

```

Then rename the .conf file of the service that you want to disable to something else. I do it like this.

```

$sudo mv sshd.conf sshd.conf.off

```

Now reboot and check using the following command;

```

sudo netstat -ltunp

```

sshd should not be listed in there.

OK, that's cool, and makes sense. Thanks for sharing :)

I looked through the upstart [Getting Started guide]("http://upstart.ubuntu.com/getting-started.html"), the [FAQ]("http://upstart.ubuntu.com/faq.html") and took a quick look at the [wiki]("http://upstart.ubuntu.com/wiki/"), but didn't find anything on this topic.

---

### Post by tomiq on 2010-10-19
This upstart thingy should clearly be better documented (maybe by a [http://www.ubuntu.com/community/Upstart](http://www.ubuntu.com/community/Upstart) document?).

Well the main documentation can be found at the project site: [http://upstart.ubuntu.com/](http://upstart.ubuntu.com/)
Overview:                  [http://upstart.ubuntu.com/getting-started.html](http://upstart.ubuntu.com/getting-started.html)
More Details on WIKI: [http://upstart.ubuntu.com/wiki/](http://upstart.ubuntu.com/wiki/)

See other posts on ubuntuforums here:
[http://ubuntuforums.org/showthread.php?t=1351501](http://ubuntuforums.org/showthread.php?t=1351501)
and here:
[http://ubuntuforums.org/showthread.php?t=1305659&page=2](http://ubuntuforums.org/showthread.php?t=1305659&page=2)



I have tweaked my services .conf files both ways as the posts suggested:
either added some new event as a dependency of starting a service (one guide suggests word 'never') or disabled the service completely by renaming its configuration file to different suffix.

Example of disabling GDM:
```
# gdm - GNOME Display Manager
#
# The display manager service manages the X servers running on the
# system, providing login and auto-login services

description    "GNOME Display Manager"
author        "William Jon McCann <mccann@jhu.edu>"

start on (x11-enabled
          and started dbus
          and (drm-device-added card0 PRIMARY_DEVICE_FOR_DISPLAY=1
               or stopped udevtrigger))
stop on (x11-disabled
          or runlevel [016])
```This approach has the advantage that I can trigger these x11-enabled or disabled events as I wish -- but that's something I will do in the evening, we'll see.

I have to reload the Upstart service definitions to catch the changes:
```
initctl reload
```.

I could now start the GDM by firing events with
```
initctl emit x11-enabled
```.

The other and maybe the more promising option is to implement the custom startup of GDM by creating a wrapper service (/etc/init/x11-enabled.conf) that would have been started manually or via some other triggers (VNC service starts up, etc.).
The /etc/init/gdm.conf would be updated accordingly:
```

# gdm - GNOME Display Manager
# ...
start on (started x11-enabled
          and started dbus
          and (drm-device-added card0 PRIMARY_DEVICE_FOR_DISPLAY=1
               or stopped udevtrigger))
stop on (stopped x11-enabled
          or runlevel [016])

```As a result GDM service would have start up or shutdown along with some other 'x11-enabled' service.

```
initctl start x11-enabled
```Do mention however that the services that are not yet ported to upstart remain managed by /etc/rc.d or whatsitsname, so in meantime we have to use both configuration mechanisms.
Just compare what says service (systemV init implementation) or initctl:
```

# Upstart version
initctl list;
# SysV version
services --status-all
# or
chkconfig --list
# All SystemV running services which would be on after reboot:
chkconfig --list | grep $(runlevel | awk '{ print $2}'):on

```I have digged further and didn't find any GUI for upstart configuration -- this means we either have to wait for it or write small pieces ourselves.
Just search for it if you don't believe me -- [http://www.google.com/search?q=upstart+configuration+gui](http://www.google.com/search?q=upstart+configuration+gui) -- and if your search was successfull it probably means that this post is really old :-)


Anyway other info about using Upstart can be digged from man:
man init (or upstart)
man initctl
man signal



Must digg deeper, maybe code some tools.
Enjoy unixing.

---

### Post by Ben Jao Ming on 2011-02-20
I have made a little post about the different ways that services are enabled/disabled in Ubuntu. The reason was that I ran into 3 different ways of launching the same program within the past 3 versions of Ubuntu :) Not to say that everything is that bad, and Upstart is certainly a powerful new player. But for now, it can be quite confusing to get rid of a service :)

[http://overtag.dk/wordpress/2011/02/headaches-over-disablingenabling-services-init-d-scripts-in-ubuntu-10-10/](http://overtag.dk/wordpress/2011/02/headaches-over-disablingenabling-services-init-d-scripts-in-ubuntu-10-10/)

---

### Post by cepal on 2011-11-04
> **Ben Jao Ming said:**
> I have made a little post about the different ways that services are enabled/disabled in Ubuntu. The reason was that I ran into 3 different ways of launching the same program within the past 3 versions of Ubuntu :) Not to say that everything is that bad, and Upstart is certainly a powerful new player. But for now, it can be quite confusing to get rid of a service :)

[http://overtag.dk/wordpress/2011/02/headaches-over-disablingenabling-services-init-d-scripts-in-ubuntu-10-10/](http://overtag.dk/wordpress/2011/02/headaches-over-disablingenabling-services-init-d-scripts-in-ubuntu-10-10/)

Hi Ben,
great hints, thanks a lot. Just one note: I think the "stop on" upstart section should never be commented out.

The reason is you still might start the daemon explicitly (manually) and then during shutdown it might not be stopped at the appropriate moment (consequentially correct according to the design) which might result in unpredictable issues (slower shutdown is the least harmful, data loss/corruption if e.g. a database gets a sigkill termination at the end of shutdown, or even a system freeze during shutdown caused by a deadlock situation).

Cheers,
CePal

---

### Post by debd on 2011-11-04
update-rc.d is the program to be used to install, remove and disable init scripts.
to disable a service say, the pure-ftp deamon (pure-ftpd) at start-up, use ```
update-rc.d -f pure-ftpd remove
```for more info see the man page of update-rc.d

---

### Post by danmbox on 2012-01-18
> **debd said:**
> update-rc.d is the program to be used to install, remove and disable init scripts.
to disable a service say, the pure-ftp deamon (pure-ftpd) at start-up, use ```
update-rc.d -f pure-ftpd remove
```for more info see the man page of update-rc.d

Uh, no. update-rc.d works for /etc/init.d services, but not for upstart (/etc/init) services. I guess you didn't read the thread before posting?

The problem is that to disable upstart services, you HAVE TO either delete or modify /etc/init/job.conf. This causes problems when upgrading the corresponding package.

---

