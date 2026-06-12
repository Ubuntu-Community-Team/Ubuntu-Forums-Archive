---
title: "how to fix 'public key is not available error"
date: 2010-05-05
forum: General Help
---

### Post by mjsilverstri on 2010-05-05
When I do 'sudo apt-get update' I get this error now:

```
Hit http://ppa.launchpad.net lucid/main Packages                         
Hit http://ppa.launchpad.net lucid/main Packages
Fetched 116kB in 1s (70.5kB/s)
Reading package lists... Done
W: GPG error: http://ppa.launchpad.net lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 1A0771178279047A
```

Can you please tell me how to fix it?

---

### Post by dino99 on 2010-05-05
> **mjsilverstri said:**
> When I do 'sudo apt-get update' I get this error now:

```
Hit http://ppa.launchpad.net lucid/main Packages                         
Hit http://ppa.launchpad.net lucid/main Packages
Fetched 116kB in 1s (70.5kB/s)
Reading package lists... Done
W: GPG error: http://ppa.launchpad.net lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 1A0771178279047A
```

Can you please tell me how to fix it?

if you have installed a ppa repo, maybe you need to read the howto on that ppa :lolflag:

---

### Post by WorMzy on 2010-05-05
I don't know if this will help, but open Software Sources from System -> Administration, and change the Download server that you're using.

---

### Post by mjsilverstri on 2010-05-07
> **dino99 said:**
> if you have installed a ppa repo, maybe you need to read the howto on that ppa :lolflag:

Can you please tell me how to remove the one which has problem?
I don't know how to do that.

Thank you.

---

### Post by garvinrick4 on 2010-05-07
Code:

gksudo gedit /etc/apt/sources.list


put a # in front of line you want to comment and it will not be read, do not forget to hit save.

---

### Post by captainron042 on 2010-05-19
I am trying to get a DVD to play, and trying to make sure medibuntu key is updated.

I'm having the same problem. I changed my sources to US instead of main server. I still got the error message.


This is what I have in my sources list. I do not see this key that is in the error.

***********************************

#opera
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com F9A2F76A9D1A0061
# deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) lenny non-free # disabled on upgrade to karmic

#chromium-browser
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 5A9BF3BB4E5E17B5
# deb [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) karmic main # disabled on upgrade to karmic

#google
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com A040830F7FAC5991
# deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable main non-free # disabled on upgrade to karmic

#empathy
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com FA3A1271
# deb [http://ppa.launchpad.net/telepathy/ppa/ubuntu](http://ppa.launchpad.net/telepathy/ppa/ubuntu) karmic main # disabled on upgrade to karmic
# deb-src [http://ppa.launchpad.net/telepathy/ppa/ubuntu](http://ppa.launchpad.net/telepathy/ppa/ubuntu) karmic main # disabled on upgrade to karmic

#pidgin
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 7FB8BEE0A1F196A8
# deb [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu) karmic main # disabled on upgrade to karmic

#emesene 1.5
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0CC1223EE2314809
# deb [http://ppa.launchpad.net/bjfs/ppa/ubuntu](http://ppa.launchpad.net/bjfs/ppa/ubuntu) karmic main # disabled on upgrade to karmic
# deb-src [http://ppa.launchpad.net/bjfs/ppa/ubuntu](http://ppa.launchpad.net/bjfs/ppa/ubuntu) karmic main # disabled on upgrade to karmic

#gnome-globalmenu
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 7889D725DA6DEEAA
# deb [http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu](http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu) karmic main # disabled on upgrade to karmic

#gnome-do
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 28A8205077558DD0
# deb [http://ppa.launchpad.net/do-core/ppa/ubuntu](http://ppa.launchpad.net/do-core/ppa/ubuntu) karmic main # disabled on upgrade to karmic

#nautilus-dropbox
# deb [http://linux.getdropbox.com/ubuntu](http://linux.getdropbox.com/ubuntu) karmic main # disabled on upgrade to karmic

# Ubuntu One Beta PPA sources
# deb [http://ppa.launchpad.net/ubuntuone/beta/ubuntu](http://ppa.launchpad.net/ubuntuone/beta/ubuntu) karmic main # disabled on upgrade to karmic
# deb-src [http://ppa.launchpad.net/ubuntuone/beta/ubuntu](http://ppa.launchpad.net/ubuntuone/beta/ubuntu) karmic main # disabled on upgrade to karmic

#gnome-colors theme
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 2D79F61BE8D31A30
# deb [http://ppa.launchpad.net/gnome-colors-packagers/ppa/ubuntu](http://ppa.launchpad.net/gnome-colors-packagers/ppa/ubuntu) karmic main # disabled on upgrade to karmic
# deb-src [http://ppa.launchpad.net/gnome-colors-packagers/ppa/ubuntu](http://ppa.launchpad.net/gnome-colors-packagers/ppa/ubuntu) karmic main # disabled on upgrade to karmic

##Themes du ZgegBlog: Project Bisigi
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 6E871C4A881574DE
# deb [http://ppa.launchpad.net/bisigi/ppa/ubuntu](http://ppa.launchpad.net/bisigi/ppa/ubuntu) karmic main # disabled on upgrade to karmic
# deb-src [http://ppa.launchpad.net/bisigi/ppa/ubuntu](http://ppa.launchpad.net/bisigi/ppa/ubuntu) karmic main # disabled on upgrade to karmic

# disper tool multiple graphical displays
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 66D5C734F6EFB904
# deb [http://ppa.launchpad.net/wvengen/ppa/ubuntu](http://ppa.launchpad.net/wvengen/ppa/ubuntu) jaunty main
# deb-src [http://ppa.launchpad.net/wvengen/ppa/ubuntu](http://ppa.launchpad.net/wvengen/ppa/ubuntu) jaunty main

# Virtualbox
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com DCF9F87B6DFBCBAE
# deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) karmic non-free # disabled on upgrade to karmic

#Freenx Team (freenx, nxagent - remote X)
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 2A8E3034D018A4CE
# deb [http://ppa.launchpad.net/freenx-team/ubuntu](http://ppa.launchpad.net/freenx-team/ubuntu) karmic main # disabled on upgrade to karmic
# deb-src [http://ppa.launchpad.net/freenx-team/ubuntu](http://ppa.launchpad.net/freenx-team/ubuntu) karmic main # disabled on upgrade to karmic

#Back In Time
# deb [http://le-web.org/repository](http://le-web.org/repository) stable main # disabled on upgrade to karmic

#shutter
# deb [http://ppa.launchpad.net/shutter/ppa/ubuntu](http://ppa.launchpad.net/shutter/ppa/ubuntu) karmic main # disabled on upgrade to karmic


#Terminator
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 978228591BD3A65C
# deb [http://ppa.launchpad.net/gnome-terminator/ppa/ubuntu](http://ppa.launchpad.net/gnome-terminator/ppa/ubuntu) karmic main # disabled on upgrade to karmic

#Drizzle
# deb [http://ppa.launchpad.net/drizzle-developers/ppa/ubuntu](http://ppa.launchpad.net/drizzle-developers/ppa/ubuntu) karmic main # disabled on upgrade to karmic
# deb-src [http://ppa.launchpad.net/drizzle-developers/ppa/ubuntu](http://ppa.launchpad.net/drizzle-developers/ppa/ubuntu) karmic main # disabled on upgrade to karmic

#subversion 1.6
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 6298AD34413576CB
# deb [http://ppa.launchpad.net/anders-kaseorg/subversion-1.6/ubuntu](http://ppa.launchpad.net/anders-kaseorg/subversion-1.6/ubuntu) karmic main # disabled on upgrade to karmic
# deb-src [http://ppa.launchpad.net/anders-kaseorg/subversion-1.6/ubuntu](http://ppa.launchpad.net/anders-kaseorg/subversion-1.6/ubuntu) karmic main # disabled on upgrade to karmic

# cassandra nosql db
# deb [http://people.apache.org/~eevans/debian](http://people.apache.org/~eevans/debian) cassandra/ # disabled on upgrade to karmic
# deb-src [http://people.apache.org/~eevans/debian](http://people.apache.org/~eevans/debian) cassandra/ # disabled on upgrade to karmic

# MySQL Workbench
# deb [ftp://ftp.mysql.com/pub/mysql/download/gui-tools/ubuntu/](ftp://ftp.mysql.com/pub/mysql/download/gui-tools/ubuntu/) binary/
# deb-src [ftp://ftp.mysql.com/pub/mysql/download/gui-tools/ubuntu/](ftp://ftp.mysql.com/pub/mysql/download/gui-tools/ubuntu/) source/

deb [http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu](http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu) lucid main
deb-src [http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu](http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu) lucid main
deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) lucid-getdeb games

deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid free non-free
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid free non-free

---

