---
title: "netbook-launcher does not launch"
date: 2010-05-10
forum: General Help
---

### Post by nrune on 2010-05-10
On upgrade to Lucid the netbook-launcher gives the following error:

```
nrune@nrune-netbook:~$ netbook-launcher
** (process:2251): DEBUG: OpenGL renderer string: ION LE/PCI/SSE2

(netbook-launcher:2251): libnetbook-launcher-DEBUG: CONFIG: Low graphics mode: False
(netbook-launcher:2251): libnetbook-launcher-DEBUG: CONFIG: Font dpi: 96.000000
(netbook-launcher:2251): libnetbook-launcher-DEBUG: CONFIG: Font changed: Sans 10

(netbook-launcher:2251): libnetbook-launcher-DEBUG: CONFIG: Connecting to ConsoleKit for suspend/resume restarting

(netbook-launcher:2251): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

```

Please help

---

### Post by VeeDubb on 2010-05-10
More information is usually helpful.

What did you install it on?

How did you upgrade?  Clean install, upgrade through the update manage, etc?

What did you upgrade from?  karmic or the old LTS?

---

### Post by nrune on 2010-05-10
What did you install it on?

HP mini 311

How did you upgrade? Clean install, upgrade through the update manage, etc?

Upgrade Manger

What did you upgrade from? karmic or the old LTS? 

Karmic

Here's the bug.
[https://bugs.launchpad.net/ubuntu/+source/netbook-launcher/+bug/538297](https://bugs.launchpad.net/ubuntu/+source/netbook-launcher/+bug/538297)

---

### Post by VeeDubb on 2010-05-10
Well, it should work fine on a 311, and it doesn't look like you did anything foolish with your upgrade.

So, the only thing I can really suggest is that you do what they said on the bug page.  Try to get a backtrace, attach it to the bug report and post it here.

---

### Post by tommihl on 2010-06-18
I have this same problem. It appeared once I changed Appearance settings to the finest. Have been using this like a year and no problems. So how do I reset reset settings? ```
netbook-launcher-efl
``` works just fine.

EDIT After a reboot theres no background even though one is selected :S ```
sudo pkill -9 netbook-launcher
``` Doesnt do anything :S Really dont understand this.

---

