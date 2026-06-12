---
title: "Internet/Network dies after about 10 Mins?"
date: 2006-04-05
forum: General Help
---

### Post by tooleh on 2006-04-05
Ok so I have one network card (eth0 - Nvidia nForce2 onboard networking)...which worked fine, but now my internet just dies after using it for about 10 mins :S

Net is fine on windows, and rebooting ubuntu fixes the problem (for 10 mins, anyway).

Here are my dmesg logs:

[http://pastebin.com/642128](http://pastebin.com/642128)
(this was taken with my other card, eth1 in, which I removed to see if it would fix the problem, but it didn't. [which is why there are entries for eth1]).

[http://pastebin.com/642209](http://pastebin.com/642209)
A slightly more recent log.


Thanks for having a look !

---

### Post by swytz on 2007-06-02
I'm having the same problem, I have two nForce2 onboard network devices.  I notice there are a lot of other people on gentoo forums having the same issue with their kernels.

I notice I can speed up the network card dying by downloading a large file such as a 600mb ISO.  Linux is unable to ever reach the 600mb mark no matter how many times I try before I have to reboot.

[http://forums.fedoraforum.org/showthread.php?t=18473](http://forums.fedoraforum.org/showthread.php?t=18473)

The link above had a guy who fixed the problem by installing another network card.

I would prefer to use my onboard nForce2 nic, but it seems that Linux hates them.

It's really unfortunate as I was looking forward to using Linux as my main workstation =(

---

### Post by Indigo_Data on 2008-04-17
I had the same issue, the network dies after transfering a large ftp file. I have a Gigabyte MB (Nvidia chipset) and adding another nic didnt fix it. It still died. I updated the MB bios from F10 to F11f ( the latest) and it fixed it. BTW I'm running Gutsy 7.10 Server AMDX2 CPU. I'm new to Ubuntu. I have run Slackware for years and recently changed. :)

JD

---

