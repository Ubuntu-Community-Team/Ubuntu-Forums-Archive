---
title: "Linux &amp; GPS"
date: 2010-06-10
forum: General Help
---

### Post by arron on 2010-06-10
Im wanting to get into Geocaching with my family.  Im looking at buying a GPS to find some of the caches out there.

What GPS's are compatable with Linux for updates, logging and any other general useage?

As well what programs would people recomend to help log / display all our adventures downloaded or uploaded to the GPS?

I run only Linux now, so Windows is not really an option.  Well i supose there is virtualbox, which I would prefer not to do.

I would like ease of use so the whole family can get involved both GPS and pc side so any input is welcomed.  

Thanks

---

### Post by tgalati4 on 2010-06-10
Open a terminal:

apt-cache search gps

I use gpxview with my nokia n800.  I don't think it's been ported to Debian.  Most gps units will dump coordinates via usb using gpsd daemon.

Try gpsdrive with a usb-gps hockey puck on a laptop.

Also:

apt-cache search geocache

Try geotoad and [http://openstreetmap.org](http://openstreetmap.org)

---

### Post by baddnady23 on 2010-06-10
What kind of GPS will you be using?

---

### Post by stafio on 2010-06-10
QLandkarte GT is available in the repositories, as of the Lucid release. I haven't used it extensively yet, but it seems to work fairly well. I think it's only for Garmin devices, but I'm not 100% sure.

---

### Post by stafio on 2010-06-11
I just came across a Linux substitute for the Garmin Communicator Plugin: [http://www.andreas-diesner.de/garminplugin/](http://www.andreas-diesner.de/garminplugin/). It hasn't been tested with the eTrex Legend HCx, which is what I have. Hopefully it works.

---

### Post by ocm_ott on 2010-07-04
> **arron said:**
> Im wanting to get into Geocaching with my family.  Im looking at buying a GPS to find some of the caches out there.

What GPS's are compatable with Linux for updates, logging and any other general useage?

As well what programs would people recomend to help log / display all our adventures downloaded or uploaded to the GPS?

I run only Linux now, so Windows is not really an option.  Well i supose there is virtualbox, which I would prefer not to do.

I would like ease of use so the whole family can get involved both GPS and pc side so any input is welcomed.  

Thanks

I'm a very avid geocacher. I'm not sure if you've heard of GSAK for Windows, but after my switch to Ubuntu[ I've started my own similar project]("http://sourceforge.net/projects/opencachemanage/").

We use an eTrex and a Colorado 300. The one piece of glue that you'll need for the eTrex is "gpsbabel", which exists in the repositories. A lot of linux software, including my own OCM,  needs it to send waypoints to machines like the eTrex. The other thing you'll need to do for the etrex if you're using Karmic or earlier is follow [the instructons here ]("http://www.gpsbabel.org/os/Linux_Hotplug.html")to fix a permission problem in talking to the device if you aren't root. This problem doesn't seem to happen in Lucid. 

[http://sourceforge.net/projects/opencachemanage/](http://sourceforge.net/projects/opencachemanage/)

---

### Post by giddyup306 on 2010-07-04
> **stafio said:**
> I just came across a Linux substitute for the Garmin Communicator Plugin: [http://www.andreas-diesner.de/garminplugin/](http://www.andreas-diesner.de/garminplugin/). It hasn't been tested with the eTrex Legend HCx, which is what I have. Hopefully it works.

After I update, and try to install it says:

E: Couldn't find package garminplugin

---

