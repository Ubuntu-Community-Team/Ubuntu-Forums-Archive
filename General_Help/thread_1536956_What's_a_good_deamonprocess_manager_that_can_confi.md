---
title: "What's a good deamon/process manager that can configure daemon autostart?"
date: 2010-07-22
forum: General Help
---

### Post by Kurtosis on 2010-07-22
Solution:

1.  Keep the base install clean, never install any servers to it, only desktop apps that don't run in the background.  Use [virtual machines]("http://forums.virtualbox.org/viewtopic.php?f=10&t=34185&p=152881#p152881") to install, work with, and/or experiment with servers.  There will be a few exceptions like Wine, but they can be managed (started/stopped) as needed.

2.  Use *chkconfig* to configure the services that run at startup.  Use *htop* to see and stop currently running processes.  Neither comes with Ubuntu, must be installed manually after installation.

------------Original Question------------
Problem:  I like to download tons of stuff from the repo's and experiment with it, but anytime the thing I download is daemon-based, it seems to start itself automatically and run continuously, even when I want to put it away for a while and do other stuff.  This is starting to add up, I'd like a better way to manage all these daemons.

For example, does Ubuntu (or Linux in general) have anything like Windows' Services Control Panel, that lets you see all the services available, and configure them to Autostart, Manual Start, or Disabled?

I know I can view and kill daenons from System Monitor, top, htop, ps -A, kill -9, but when I reboot they're right back running again.  (Sometimes rebooting is the only thing I can find to fix a niggling problem, like Gnome-Do suddenly failing to open Nautilus or Opera).

I've checked System->Preferences->Startup Applications too, and it seems to cover stuff that is more core to the distro, and not so much random servers and whatnot.  I see you can add stuff, but I was hoping for something that could already see all the running process and provide a way to configure each.

For example, some of the daemons I'm experimenting with that I want more control over:

/usr/lib/erlang/erts-5.7.4/bin/beam.smp
nagios
mythbackend
snort
munin
stompserver
chef
puppetmasterd
murmurd (mumble server)
trytond
postgresql
pgpool
mysqld
ulogd
nginix
apache2
memcached
memcachedb
exim4
lircd
sshd

Or are these servers only configurable within each application's config files?

---

