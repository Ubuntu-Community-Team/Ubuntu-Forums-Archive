---
title: "Log file viewer spam that is leading to system performance issues"
date: 2011-02-01
forum: General Help
---

### Post by Hariharakadan on 2011-02-01
The Spam:
[http://paste.ubuntu.com/561007/](http://paste.ubuntu.com/561007/)

The entries are appearing so frequently that the System Log Viewer has to consume 100% of CPU usage as well as hanging when retrieving the logs from each of the entries.
Debug, Kern, Syslog and Messages seems to be the main ones that are creating entries at the rate of 2 per second by the looks of it.

Is there any way of squelching this over-flow of logs?

[http://paste.ubuntu.com/561011/](http://paste.ubuntu.com/561011/) LSHW

By system performance issues I mean it brings Ubuntu almost to a crawl. This problem began after I upgraded from 10.04 to 10.10.

If there is any more information that I need to provide please let me know.

---

### Post by bodhi.zazen on 2011-02-01
Typically one gets that message if you eject a CD without unmounting it first.

If this is not the case, try adding "noapic" to your boot line.

Reboot -> At the grub screen hit e to edit the line, on the kernel line, where you see ro quiet splash, add noapic.

"ro quiet splash noapic"

If this works, we can add the option to grub.

---

### Post by Hariharakadan on 2011-02-01
No luck with noapic added to grub. Sorry. ; ;

-Edit Also, there has been no media in either of the drives I have been using. It just starts as soon as Ubuntu is up it would seem.

---

### Post by bodhi.zazen on 2011-02-01
I would file a bug report and try a different kernel.

---

