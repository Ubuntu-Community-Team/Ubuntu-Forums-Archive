---
title: "wake on lan"
date: 2009-10-13
forum: General Help
---

### Post by chaosc on 2009-10-13
Hey guys i have ubuntu server running 24x7.  I want to be able to wake up other computers on my network.  what software do i need to load on the server so i can from the command line just type it out and turn the pc on.  is there a apt-get program i can load?
thanks

---

### Post by Lars Noodén on 2009-10-13
wakeonlan is the one mentioned here in the tutorial:
[http://ubuntuforums.org/showthread.php?t=234588](http://ubuntuforums.org/showthread.php?t=234588)

but there are two others, if you do not write your own (e.g. using CPAN's [Net::Wake]("http://search.cpan.org/~clintdw/Net-Wake-0.02/lib/Net/Wake.pm") or similar)
powerwake - remotely wake a napping system
etherwake - A little tool to send magic Wake-on-LAN packets

I've used wake-on-lan a bit, but from a different package.

---

