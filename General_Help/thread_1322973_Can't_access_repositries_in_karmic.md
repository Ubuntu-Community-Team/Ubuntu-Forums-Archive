---
title: "Can't access repositries in karmic"
date: 2009-11-11
forum: General Help
---

### Post by leeg on 2009-11-11
I've just done a clean install of Karmic on my Acer Aspire Revo and I can't connect to the repositries. I have disable my ipv6 in firefox as I couldn't see any webpages and that worked fine, so I thought I'd try a system wide disable of the ipv6 using the many posts on these forums but no joy. 

I seem to remember having to disable the ipv6 when installed jaunty so I was pretty sure that this would be the problem but I'm at a lost at what to try next.

PS Is there any way that I can see if IPV6 is disabled

---

### Post by jerrrys on 2009-11-11
have you tried changing your download source?

how bout a "sudo apt-get update"?

---

### Post by leeg on 2009-11-11
hi
 
yes tried from both main server & uk server with no luck

---

### Post by jerrrys on 2009-11-11
im not sure whats going on so if you can beer with me, like to do some fishing...

can you post a screen shot of your third party source list?

---

### Post by leeg on 2009-11-14
Sorry been away for a few days, I reinstalled jaunty and that connected to the repositries straight away (obviously nothing to do with ipv6), so I thought I would try an upgrade to Karmic, big mistake it wouldn't even get to the splash screen!!! So I have re(clean)installed karmic and I am back where I was to start with. Here are the screen shots of my software sources.......

---

### Post by coffeecat on 2009-11-14
This sounds as though you've been hit with an IPv6 DNS-resolving bug which is affecting a minority of users because the fault seems to be in the router firmware. That being said, something in Karmic has unmasked this problem and since IPv6 was enabled in Jaunty (and is by default in Vista, W7 and MacOSX) and Jaunty worked fine, there needs to be a bug-fix in Karmic ASAP. Have a look at this:

[https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/417757](https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/417757)

It's marked as confirmed/high so hopefully a bug-fix will come through in due course.

Tbh I'm out of my depth here, but post #7 seems to explain it well. In the meantime there are a couple of workarounds you might want to try. As you found, disabling IPv6 in Firefox sorted Firefox out, but not your package managers. You need a system-wide workaround.

Try:

* Open DNS works for some - it's referenced in that thread.
* Set a fixed IP address for your computer and add your DNS IP addresses manually.
* Disable IPv6 system-wide with a simple edit of a system file. I haven't got the details but a search of the forum might throw something up. Or it might be in that Launchpad thread. *** **EDIT:** - sorry. Just noticed you tried that. But perhaps the ones you tried weren't good for Karmic. Keep looking. 
* Have you got (or can you borrow) another router of a different make to try?

---

### Post by garvinrick4 on 2009-11-14
What does it do when you run a traceroute or a ping of a ubuntu mirror. In Admin/network tools in GUI. If not there in Edit Menu's for Administration. Would be interesting to see.

Network tools will show you IPv6.

---

### Post by leeg on 2009-11-14
ok, so I managed to connect to the repositries by using the " find best server" button. This has allowed me to enable my Nvidia drivers (and I have to say the system flies now!) I went to do a system update and it found all the updates but wouldn't download them..... so I have tried to disable the ipv6 system wide and the same thing happened....then I retried the find best server" and wahoo the updates have downloaded. whether or not I will continue to get updates or if I will have to look futher at the ipv6 problem I'll have to wait and see.....

---

### Post by leeg on 2009-11-14
**update** have just tried to install the flash player in firefox and it just sits there not downloading so I guess I'm still looking for a fix.

---

### Post by leeg on 2009-11-14
screenshot of network tools
ping comes back as can't find network address, but it pings ok when I do another website

---

### Post by wojox on 2009-11-14
Did you edit /etc/default/grub and included the ipv6.disable=1 in the "quiet splash" quotes. And then run sudo update-grub? Reboot

---

### Post by leeg on 2009-11-14
> **wojox said:**
> Did you edit /etc/default/grub and included the ipv6.disable=1 in the "quiet splash" quotes. And then run sudo update-grub? Reboot

yep, tried that - no luck

---

### Post by garvinrick4 on 2009-11-14
What country are you from? Trying to see the best bandwidth for
you are located.

---

### Post by jeb800e on 2009-11-14
System < Administration < Software Sources

---

### Post by leeg on 2009-11-15
located in uk

---

### Post by leeg on 2009-11-15
this is the error i get when i try to install flash

---

### Post by garvinrick4 on 2009-11-16
Here are the mirrors looks like University of Kent has largest bandwidth but one week behind. Two of the 1 gig bandwidth up to date. Give them a try see where the best service lies. Some more congested than others.


        8 Gbps                             11                      mirrors                                           [University Of Kent UK Mirror Service]("https://launchpad.net/ubuntu/+mirror/uk-mirror-service")                             [http]("http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/")           [ftp]("ftp://ftp.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/")           [rsync]("rsync://rsync.mirrorservice.org/archive.ubuntu.com/ubuntu/")                  2 Gbps                             One week behind                                           [Bytemark Hosting]("https://launchpad.net/ubuntu/+mirror/bytemark-archive")                             [http]("http://mirror.bytemark.co.uk/ubuntu/")           [ftp]("ftp://mirror.bytemark.co.uk/ubuntu/")           [rsync]("rsync://mirror.bytemark.co.uk/ubuntu/")                  1 Gbps                             Up to date                                           [XILO Communications Ltd.]("https://launchpad.net/ubuntu/+mirror/mirror.as29550.net-archive")                             [http]("http://mirror.as29550.net/archive.ubuntu.com/")           [ftp]("ftp://mirror.as29550.net/archive.ubuntu.com/")                             1 Gbps                             Up to date                                           [Oxford University Computing Services]("https://launchpad.net/ubuntu/+mirror/mirror.ox.ac.uk-archive")                             [http]("http://mirror.ox.ac.uk/sites/archive.ubuntu.com/ubuntu/")           [ftp]("ftp://mirror.ox.ac.uk/sites/archive.ubuntu.com/ubuntu/")           [rsync]("rsync://mirror.ox.ac.uk/sites/archive.ubuntu.com/")                  1 Gbps                             One week behind                                           [Goscomb Technologies Limited]("https://launchpad.net/ubuntu/+mirror/mirror.sov.uk.goscomb.net-archive")                             [http]("http://mirror.sov.uk.goscomb.net/ubuntu/")           [ftp]("ftp://mirror.sov.uk.goscomb.net/ubuntu/")                             1 Gbps                             Six hours behind                                           [Ticklers.Org]("https://launchpad.net/ubuntu/+mirror/ticklers")                             [http]("http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/")           [ftp]("ftp://ftp.ticklers.org/archive.ubuntu.org/ubuntu/")           [rsync]("rsync://ftp.ticklers.org/archive.ubuntu.org/ubuntu/")                  1 Gbps                             One week behind                                           [datahop.it]("https://launchpad.net/ubuntu/+mirror/ubuntu-archives.datahop.it-archive")                             [http]("http://ubuntu-archive.datahop.it/ubuntu/")           [ftp]("ftp://ubuntu-archive.datahop.it/ubuntu/")           [rsync]("rsync://ubuntu-archive.datahop.it/ubuntu/")                  1 Gbps                             Up to date                                           [Canonical Ltd]("https://launchpad.net/ubuntu/+mirror/archive.ubuntu.com")                             [http]("http://archive.ubuntu.com/ubuntu/")           [ftp]("ftp://archive.ubuntu.com/ubuntu/")           [rsync]("rsync://archive.ubuntu.com/ubuntu/")                  100 Mbps                             Up to date                                           [The Positive Internet Company]("https://launchpad.net/ubuntu/+mirror/ubuntu.positive-internet.com-archive")                             [http]("http://ubuntu.positive-internet.com/ubuntu/")                                        100 Mbps                             One week behind                                           [Retrosnub Internet Services]("https://launchpad.net/ubuntu/+mirror/ubuntu.retrosnub.co.uk-archive")                             [http]("http://ubuntu.retrosnub.co.uk/ubuntu/")           [ftp]("ftp://ubuntu.retrosnub.co.uk/ubuntu/")           [rsync]("rsync://ubuntu.retrosnub.co.uk/ubuntu/")                  100 Mbps                             One day behind                                           [Virgin Media]("https://launchpad.net/ubuntu/+mirror/ubuntu.virginmedia.com-archive")                             [http]("http://ubuntu.virginmedia.com/archive/")           [ftp]("ftp://mirrors.virginmedia.com/mirrors/ubuntu/archive")                             100 Mbps                             One week behin

---

