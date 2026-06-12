---
title: "Install Debian Sid from netinstall cd"
date: 2009-10-09
forum: General Help
---

### Post by nikhilbhardwaj on 2009-10-09
i've read  that you can only install sid after installing some version of debian
but someone says that you can also install from a net-install cd
by changing the repositories before installing
 
is it possible 
or must i first install lenny and then sid
 
is there a netinstall cd for ubuntu 9.10 yet??

---

### Post by mikewhatever on 2009-10-09
Let's google:

[Karmic netboot iso]("http://archive.ubuntu.com/ubuntu/dists/karmic/main/installer-i386/current/images/netboot/mini.iso")

[Debian SID FAQ]("http://wooledge.org/~greg/sidfaq.html")

> How do I install sid?

The canonical answer is: You don't. You can only upgrade to it from stable or testing. You do that by editing /etc/apt/sources.list and changing your sources from stable to unstable.

There are some unofficial "sid ISO images" out there. They are dangerous, unofficial and obsolete (by definition!). Stay away from them.

It may also be possible to install sid packages instead of testing packages if you're using a net install from the testing branch. This is not supported, but if you want to try it, you're free to do so. It's your machine, after all. Just don't cry if it breaks.


---

### Post by nikhilbhardwaj on 2009-10-10
ya i know that about sid
but can't i install with a live cd

anyway
thanks for the 9.10 netboot iso link

---

