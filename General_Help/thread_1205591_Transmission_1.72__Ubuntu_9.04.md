---
title: "Transmission 1.72 / Ubuntu 9.04"
date: 2009-07-06
forum: General Help
---

### Post by ugm6hr on 2009-07-06
I have just tried to install Transmission 1.72 on Ubuntu 9.04 (-common and -gtk).

Getdeb.net have i386 .debs, which don't appear to work.

Similarly, the launchpad PPA - [http://forum.transmissionbt.com/viewtopic.php?f=13&t=5604](http://forum.transmissionbt.com/viewtopic.php?f=13&t=5604) - has the same problem.

The default menu entry **transmission %F** does nothing.

Launching from Terminal:
```
$ transmission
** Message: err: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

```

The binary **transmission** does exist in /usr/bin/ and I removed the original before trying to install the new version.

Anyone have any solutions?

---

### Post by NFblaze on 2009-07-14
Install from this PPA website each of these debs.[https://launchpad.net/~bojo42/+archive/testing/+build/1092358](https://launchpad.net/~bojo42/+archive/testing/+build/1092358)

 I believe you must do it in this order btw.

*common
*daemon
*cli
*gtk
*transmission_1.72

---

