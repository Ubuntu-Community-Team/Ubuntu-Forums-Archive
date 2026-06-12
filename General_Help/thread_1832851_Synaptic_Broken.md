---
title: "Synaptic Broken"
date: 2011-08-25
forum: General Help
---

### Post by cnj on 2011-08-25
I was using the synaptic package manager adding a new repository. I did something wrong, I think, and now I get this message:-
 
"E: Malformed line 59 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialogue to correct the problem.
E: _cache->open() failed, please report."

When I close the message synaptic closes as well. Does any one have an idea how to solve?

---

### Post by jerrrys on 2011-08-25
sudo gedit /etc/apt/sources.list

and either post this list or find line 59 and repair

---

### Post by realzippy on 2011-08-25
```
cat -n /etc/apt/sources.list
```

saves you from counting..

---

### Post by cnj on 2011-08-25
I have two windows of text. First:-

colin@colin-MS-7309:~$ sudo gedit /etc/apt/sources.list
[sudo] password for colin: 

(gedit:2443): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.730U0V': No such file or directory

(gedit:2443): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:2443): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.N3EY0V': No such file or directory

(gedit:2443): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

And second:-

# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release amd64 (20110427.1)]/ natty main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://im.archive.ubuntu.com/ubuntu/](http://im.archive.ubuntu.com/ubuntu/) natty main restricted
deb-src [http://im.archive.ubuntu.com/ubuntu/](http://im.archive.ubuntu.com/ubuntu/) natty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://im.archive.ubuntu.com/ubuntu/](http://im.archive.ubuntu.com/ubuntu/) natty-updates main restricted
deb-src [http://im.archive.ubuntu.com/ubuntu/](http://im.archive.ubuntu.com/ubuntu/) natty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://im.archive.ubuntu.com/ubuntu/](http://im.archive.ubuntu.com/ubuntu/) natty universe
deb-src [http://im.archive.ubuntu.com/ubuntu/](http://im.archive.ubuntu.com/ubuntu/) natty universe
deb [http://im.archive.ubuntu.com/ubuntu/](http://im.archive.ubuntu.com/ubuntu/) natty-updates universe
deb-src [http://im.archive.ubuntu.com/ubuntu/](http://im.archive.ubuntu.com/ubuntu/) natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://im.archive.ubuntu.com/ubuntu/](http://im.archive.ubuntu.com/ubuntu/) natty multiverse
deb-src [http://im.archive.ubuntu.com/ubuntu/](http://im.archive.ubuntu.com/ubuntu/) natty multiverse
deb [http://im.archive.ubuntu.com/ubuntu/](http://im.archive.ubuntu.com/ubuntu/) natty-updates multiverse
deb-src [http://im.archive.ubuntu.com/ubuntu/](http://im.archive.ubuntu.com/ubuntu/) natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://im.archive.ubuntu.com/ubuntu/](http://im.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse
# deb-src [http://im.archive.ubuntu.com/ubuntu/](http://im.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main
deb [http://torproject.org/torproject.org](http://torproject.org/torproject.org) "natty"
deb-src [http://torproject.org/torproject.org](http://torproject.org/torproject.org) "natty"

---

### Post by jerrrys on 2011-08-25
**Not Found**

 The requested URL /torproject.org was not found on this server.
  Apache Server at [www.torproject.org](www.torproject.org) Port 443

looks like the torproject is giving you grief.  comment out (#) the troproject and try again

---

### Post by jerrrys on 2011-08-25
cat -n /etc/apt/sources.list

nice

---

### Post by cnj on 2011-08-25
Edited line 59 and synaptic appears to run again.

Thanks for the help.

---

### Post by mhgsys on 2011-08-25
in case you want to use tor, and want to know where you gone wrong

>  You'll need to set up our package repository before you can fetch Tor. First, you need to figure out the name of your distribution. A quick command to run is lsb_release -c or cat /etc/debian_version. Here's a quick mapping:

    * Debian unstable (sid) is "sid"
    * Debian testing is "wheezy"
    * Debian 6.0 (squeeze) is "squeeze"
    * Debian 5.0 (lenny) is "lenny"
    * Ubuntu 11.04 is "natty"
    * Ubuntu 10.10 or Trisquel 4.5 is "maverick"
    * Ubuntu 10.04 or Trisquel 4.0 is "lucid"
    * Ubuntu 9.10 or Trisquel 3.5 is "karmic"
    * Ubuntu 8.04 is "hardy"

Then add this line to your /etc/apt/sources.list file:

deb     [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) <DISTRIBUTION> main

where you put the codename of your distribution (i.e. lenny, sid, maverick or whatever it is) in place of <DISTRIBUTION>.

Then add the gpg key used to sign the packages by running the following commands at your command prompt:

gpg --keyserver keys.gnupg.net --recv 886DDD89
gpg --export A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89 | sudo apt-key add -

Now refresh your sources and install Tor by running the following commands (as root) at your command prompt:

apt-get update
apt-get install tor tor-geoipdb


I'm on lucid atm , so in my case adding ```
deb http://deb.torproject.org/torproject.org lucid  main
deb http://deb.torproject.org/torproject.org experimental-lucid  main

``` to /etc/apt/sources.list works after adding the gpg keyserver keys

**in your case; change lucid main to natty main **

> mhg@mhg-desktop:~$ sudo apt-get install tor tor-geoipdb
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  polipo socat torsocks
Suggested packages:
  mixmaster xul-ext-torbutton
The following NEW packages will be installed:
  polipo socat tor tor-geoipdb torsocks
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 2,543kB/2,786kB of archives.
After this operation, 8,167kB of additional disk space will be used.
Do you want to continue [Y/n]? 


---

