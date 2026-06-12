---
title: "&quot;Waiting for network configuration&quot;"
date: 2012-03-24
forum: General Help
---

### Post by thomsmells on 2012-03-24
My version of lubuntu 11.10 has been working fine since I got it, today it's decided that it's going to wait 2 minutes at start up displaying the message.

Waiting for network configuration
Waiting a further 60 seconds for network configuration
Booting without a full network configuration

After that it comes on and the wireless works just fine (hence me not putting this in the networking section); haven't tried wired though.

I've been installing a bunch of packages today (see below), so I'm assuming it's in some way related to that, but I can't figure out how.

Any idea how I can fix/get it to boot without this message. As far as I can tell the system is working just fine. I've seen a bunch of similar error messages relating to the ubuntu 11.04-11.10 upgrade from a while ago, but I'm not sure that this is the same problem.



List of packages installed before problem started:

man-pages-3.35
kmod-5
inetutils-1.9.1
iana-etc-2.30
gdbm-1.10

---

### Post by jerrrys on 2012-03-24
This of course only happens when not connected to the WWW.

check it out

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Waiting+for+network+configuration+at+boot+startup&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Waiting+for+network+configuration+at+boot+startup&sa=Search&cof=FORID:9)

---

### Post by thomsmells on 2012-03-24
Like I said, these are all regarding the upgrade from 11.04 to 11.10, which I didn't do.

Also how can I be connected to the internet at boot? And why would it only be an issue now?

---

### Post by amjjawad on 2012-04-11
> **thomsmells said:**
> My version of lubuntu 11.10 has been working fine since I got it, today it's decided that it's going to wait 2 minutes at start up displaying the message.

Waiting for network configuration
Waiting a further 60 seconds for network configuration
Booting without a full network configuration

After that it comes on and the wireless works just fine (hence me not putting this in the networking section); haven't tried wired though.

I've been installing a bunch of packages today (see below), so I'm assuming it's in some way related to that, but I can't figure out how.

Any idea how I can fix/get it to boot without this message. As far as I can tell the system is working just fine. I've seen a bunch of similar error messages relating to the ubuntu 11.04-11.10 upgrade from a while ago, but I'm not sure that this is the same problem.



List of packages installed before problem started:

man-pages-3.35
kmod-5
inetutils-1.9.1
iana-etc-2.30
gdbm-1.10

Hi there,

I'm a member of Lubuntu Family and I also have this issue when I did this: [http://ubuntuforums.org/showpost.php?p=11832431&postcount=152](http://ubuntuforums.org/showpost.php?p=11832431&postcount=152)

I've never ever got this issue before and this is the first time. I found this thread after I was googling and trying to find a fix for this issue.

For me, I've done Mini ISO installation + Installing "lubuntu-core" + Installing "lxdm" + Installing "wicd"

I will get back to you once I find something to get rid of this :)

---

### Post by amjjawad on 2012-04-11
As promised, here is a fix that worked for me 100%

[http://ubuntuforums.org/showpost.php?p=11835741&postcount=448](http://ubuntuforums.org/showpost.php?p=11835741&postcount=448)

---

