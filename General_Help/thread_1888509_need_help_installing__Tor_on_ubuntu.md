---
title: "need help installing  Tor on ubuntu"
date: 2011-11-29
forum: General Help
---

### Post by zpata on 2011-11-29
so I installed the tor bundle only to get a message that says its outdated. I went to the tor site and it said: "If you're using Ubuntu, don't use the default packages: use our deb repository instead"  so I clicked on the "deb repository" link which led me to a section that said: "You'll need to set up our package repository before you can fetch Tor. First, you need to figure out the name of your distribution. A quick command to run is lsb_release -c or cat /etc/debian_version"   but when I run "lsb_release -c /etc/natty" in the terminal it says:  "Usage: lsb_release [options]  lsb_release: error: No arguments are permitted"   any ideas?

---

### Post by Dangertux on 2011-11-29
> **zpata said:**
> so I installed the tor bundle only to get a message that says its outdated. I went to the tor site and it said: "If you're using Ubuntu, don't use the default packages: use our deb repository instead"  so I clicked on the "deb repository" link which led me to a section that said: "You'll need to set up our package repository before you can fetch Tor. First, you need to figure out the name of your distribution. A quick command to run is lsb_release -c or cat /etc/debian_version"   but when I run "lsb_release -c /etc/natty" in the terminal it says:  "Usage: lsb_release [options]  lsb_release: error: No arguments are permitted"   any ideas?

Adding the repo for tor is done as such under Natty.


```

gksudo gedit /etc/apt/sources.list

```Add the following line

```

deb     http://deb.torproject.org/torproject.org natty main

```Then do the the following in a terminal

```

gpg --keyserver keys.gnupg.net --recv 886DDD89
gpg --export A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89 | sudo apt-key add -

```Then 

```

sudo apt-get update

```If you need full instructions for installing Tor (not the browser bundle) check here : [http://dangertux.wordpress.com/tutorials/tor-polipo-5-minute-install-guide-ubuntu-11-0411-10/](http://dangertux.wordpress.com/tutorials/tor-polipo-5-minute-install-guide-ubuntu-11-0411-10/)

Hope this helps.

---

