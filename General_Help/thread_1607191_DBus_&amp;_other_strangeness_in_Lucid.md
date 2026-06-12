---
title: "DBus &amp; other strangeness in Lucid"
date: 2010-10-27
forum: General Help
---

### Post by paul@cyberengel.com on 2010-10-27
I've been using Lucid for a few months now, (Lenovo W500, 8GB RAM & integrated Radeon HD3650 graphics).  During that time I've noticed some odd behaviour (like selecting "Shut Down" from the power icon not shutting the system down to miscellaneous commands just not working).  Based on what I've seen lately I'm wondering if I'm having problems with DBus.

First clue was my Nautilus bookmarks.  I have a couple of bookmarks that point to FTP sites I use regularly.  One, (to a system on my local GigE network) would frequently come back with DBus timeouts.  If I tried a few times it would work.  If retrying didn't work, running a simple FTP command from the command line then trying the bookmark again fixed the problem.  I figured it was something in FTP.

My next big clue was Rhythmbox.  I've been using it all along, but I've had several podcasts that fail to download.  While debugging this I noticed the following message:
> DBus error org.freedesktop.DBus.Error.NoReply
but when I tried to download the file with wget it worked fine.

So now I wonder... are the shutdown and other odd issues related to DBus?  I've tried reinstalling DBus, but that hasn't worked.

Anybody got any ideas?

Thanks.

---

