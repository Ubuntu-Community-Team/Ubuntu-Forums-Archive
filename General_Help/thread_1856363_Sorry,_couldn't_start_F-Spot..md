---
title: "Sorry, couldn't start F-Spot."
date: 2011-10-08
forum: General Help
---

### Post by fchaffin on 2011-10-08
Hi,
F-Spot is not starting up. I get a dialog titled "F-Spot Encountered a fatal error."

I removed f-spot completely, deleted all the left over f-spot config files that installed f-spot again.  I am still getting the same error.  I am pretty sure I was able to launch f-spot a month or so ago.

Here is the details behind the "F-Spot Encountered a fatal error." dialog.  Any Ideas....

----------------------------------------------------------------------------------------
An unhandled exception was thrown: Sorry, couldn't start F-Spot.

  at FSpot.Driver.Main (System.String[] args) [0x00000] in <filename unknown>:0 
.NET Version: 2.0.50727.1433

Assembly Version Information:

System.Configuration (2.0.0.0)
FSpot.Widgets (0.0.0.0)
System.Xml (2.0.0.0)
NDesk.DBus.Proxies (0.0.0.0)
gconf-sharp (2.24.0.0)
FSpot.Query (0.0.0.0)
FSpot.JobScheduler (0.0.0.0)
gdk-sharp (2.12.0.0)
NDesk.DBus.GLib (1.0.0.0)
NDesk.DBus (1.0.0.0)
gnome-vfs-sharp (2.24.0.0)
Cms (0.0.0.0)
FSpot.Core (0.0.0.0)
FSpot.Platform (0.0.0.0)
Mono.Posix (2.0.0.0)
FSpot.Utils (0.0.0.0)
System.Core (3.5.0.0)
atk-sharp (2.12.0.0)
gtk-sharp (2.12.0.0)
Mono.Addins (0.6.0.0)
System (2.0.0.0)
Mono.Addins.Setup (0.6.0.0)
glib-sharp (2.12.0.0)
f-spot (0.6.1.5)
mscorlib (2.0.0.0)

Platform Information: Linux 2.6.32-34-generic-pae i686 unknown GNU/Linux

Distribution Information:

[/etc/debian_version]
squeeze/sid

[/etc/lsb-release]
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.3 LTS"

---

### Post by directhex on 2011-10-08
Mono.Addins 0.6 on Lucid?

You've got some nonstandard packages going on here.

My guess? You're using Mono from badgerports.org, but didn't read the warning on [http://badgerports.org/news.html](http://badgerports.org/news.html)

---

### Post by fchaffin on 2011-10-08
> **directhex said:**
> Mono.Addins 0.6 on Lucid?

You've got some nonstandard packages going on here.

My guess? You're using Mono from badgerports.org, but didn't read the warning on [http://badgerports.org/news.html](http://badgerports.org/news.html)
You got it.  I do have badgerports.org enabled, which picked up the Mono 2.6 release during a recent Update Manager.  I will either downgrade Mono or upgrade F-Spot.

Thanks

---

