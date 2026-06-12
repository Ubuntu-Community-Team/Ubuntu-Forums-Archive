---
title: "Ubuntu /dev/mapper Full"
date: 2012-08-11
forum: General Help
---

### Post by HABalloonGirl on 2012-08-11
Hi,

I'm having an issue with an Ubuntu 10.04 desktop running a VirtualBox Ubuntu server.  I have booted up the computer 4 times.  The first 2 time, it was connected to the network and I got a "disk full" error where it could not run the virtual machine.  I did a df -H and found that /dev/mapper/ssl-154-root was taking up 418 GB.  I booted the computer without being connected to the network and now this section only takes up 25 GB.  

Whats going on?  The virtual machine, also, if I do a df -H, has 35% of its capacity locked up in this same location.  I've looked at other machines running 10.04 and Xubuntu, and I don't even see /dev/mapper listed when I do a df -H.  Can someone tell me what this is and how I could fix it?  The virtual machine is the only thing on there and it only takes up 11 GB of space.  

Thanks.

---

