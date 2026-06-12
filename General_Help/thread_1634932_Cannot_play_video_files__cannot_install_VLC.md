---
title: "Cannot play video files / cannot install VLC"
date: 2010-12-01
forum: General Help
---

### Post by RCXtest on 2010-12-01
Mplayer stopped working, either after system updates or after installing and removing a video web tv app.

I removed mplayer and went to install VLC:

```
andrew@office-desktop:~$ sudo apt-get check
Reading package lists... Done
Building dependency tree       
Reading state information... Done

andrew@office-desktop:~$ sudo apt-get install vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  vlc: Depends: vlc-nox (= 1.1.5-1ubuntu2~ppa1~lucid1) but it is not going to be installed
       Recommends: vlc-plugin-notify (= 1.1.5-1ubuntu2~ppa1~lucid1) but it is not going to be installed
       Recommends: vlc-plugin-pulse (= 1.1.5-1ubuntu2~ppa1~lucid1) but it is not going to be installed
E: Broken packages
andrew@office-desktop:~$
```
Anyone have any ideas?

Thanks.

---

### Post by coffeecat on 2010-12-01
According to the output you posted, vlc is wanting dependencies from a ppa repository which means that you have enabled a ppa repository that contains its own version of vlc, and that the repository itself must be inconsistent and/or badly maintained.

If you install vlc from the Ubuntu Universe repository you won't encounter these dependency problems, although you'll probably get an older version of vlc. I suggest you find out which ppa is the problem here and disable it. Then, either install the Ubuntu version of vlc or find a better maintained ppa.

---

### Post by RCXtest on 2010-12-01
Thanks for the reply.

I had these 2 repositories enabled in 'other software':

[http://ppa.launchpad.net/lucid-bleed/ppa/ubuntu](http://ppa.launchpad.net/lucid-bleed/ppa/ubuntu)
[http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu)

Unchecked them and VLC installed.

Marking as solved. Thanks.

---

