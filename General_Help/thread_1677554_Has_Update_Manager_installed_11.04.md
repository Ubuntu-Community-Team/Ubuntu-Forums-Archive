---
title: "Has Update Manager installed 11.04???"
date: 2011-01-28
forum: General Help
---

### Post by bpan123 on 2011-01-28
I installed 10.10 on this (new) system a couple of months ago.  Haven't had it attached to the network for a couple of months (for viewing documents)

Yesterday I did connect, let Update Manager do its thing (installed ~180MB of updates).  Everything went fine.  Today, was planning on installing Calibre on this and couldn't remember what version I had installed, so I checked...

**> System > About Ubuntu**  now reports that I have **11.04 (Natty Narwhal)** installed.

Is this correct?   I thought 11.04 wasn't to be released until April 2011.
Everything running fine (no obvious changes on the desktop at all)...

Your thoughts - suggestions - what have I done ?!   :confused:

Thanks, bpan

---

### Post by Krazie_kid on 2011-01-28
Hey buddy,

I realized I have the same thing, it must have happened when we updated... I do not notice that much of a difference, besides the fact that some of my wine programs are not working at all for some reason.

---

### Post by Primefalcon on 2011-01-28
no no the about documentation on 10.10 is wrong (you can verify which version you are runnin by using the command cat /etc/lsb-release) you can easily fix it though by going into /usr/share/gnome/help/libs/global.ent

use the command
```
gksudo gedit /usr/share/gnome/help/libs/global.ent
```

just update the version bit like so....
```
<!-- VERSIONS -->
<!ENTITY distro-version 'Maverick Meerkat'>
<!ENTITY distro-rev '10.10'>
<!ENTITY distro-rev-short '10.10'>
<!-- the distro-rev-short entity should not include the "LTS" in a long term release and can be used for url links --> 
<!ENTITY distro-release-date "October 2010">
<!ENTITY distro-support-date "April 2012">
<!ENTITY distro-short-codename "maverick">
<!ENTITY distro-apt-cd-name "Ubuntu 10.10_Maverick_Meerkat">
<!ENTITY linux-kernel-version "2.6.35">
```

I had this bug on my machine a while back and had to string a few greps together to find the issue

---

