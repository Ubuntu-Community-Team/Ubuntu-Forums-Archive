---
title: "Slow rsync to external USB drive"
date: 2009-10-28
forum: General Help
---

### Post by Literati on 2009-10-28
Hi everyone. I'm trying to copy some data from an internal 1TB Caviar Black drive to one that I have in an enclosure hooked up to my PC via USB 2.0

I issue the following rsync command:

sudo rsync -a --human-readable --progress /home/matt/.media/Music/ /media/disk/

And it starts the first few songs with file transfer rates of around 28MB/s, but then by the 10th song or so, it's way down to about 16kb/s or so. This can't possibly be normal, can it? I have about 100GB worth of music, and at this rate, it would take months to finish... 

Any ideas as to what's giving it the bottleneck? I'm not transferring any data over any other USB port, nor am I really using the HDDs...

---

### Post by linorics on 2009-10-28
That's not normal. One thing you could try is to Copy and paste the folder with your music to the drive. That would rule out rsync at least.

---

### Post by Literati on 2009-10-28
I tried that already. 

I seem to have spotted the problem...

> /var/log/syslog wrote:

Oct 28 14:49:18 matt kernel: [19439.028978] usb 3-1: new full speed USB device using uhci_hcd and address 3
Oct 28 14:49:18 matt kernel: [19439.152537] usb 3-1: device descriptor read/64, error -71
Oct 28 14:49:18 matt kernel: [19439.401956] usb 3-1: not running at top speed; connect to a high speed hub

I can post more of the relevant sections if necessary. In any case, all of my USB ports are USB 2.0 ports, so I googled around for the problem, and read about issuing the following commands:

rnmod ehci_hcd
rnmod uhci_hcd
modprobe ehci_hcd
modprobe uhci_hcd

because they don't get "loaded in the correct order" and this would fix it. But when I do that I get:

matt@matt:~$ rmmod ehci_hcd
ERROR: Module ehci_hcd does not exist in /proc/modules
matt@matt:~$ rmmod uhci_hcd
ERROR: Module uhci_hcd does not exist in /proc/modules
matt@matt:~$ modprobe ehci_hcd
FATAL: Module ehci_hcd not found.
matt@matt:~$ modprobe uhci_hcd
FATAL: Module uhci_hcd not found.

So then I read that the lack of that module could be a kernel issue, so I updated my kernel from 

Linux matt 2.6.28-15-generic #52-Ubuntu SMP Wed Sep 9 10:48:52 UTC 2009 x86_64 GNU/Linux

to the newest version (2.6.28-16) and I'm about to reset to see if that fixes the problem. I see that kernel 2.6.31 is out, but I'm not sure if that's "Compatible" so to speak with Ubuntu 9.04, so I didn't want to chance it and install it :P

EDIT: So, my problem is solved by one of two reasons:

2.6.28-16 is a miracle worker. 
Or, I had been reading that when using an external USB drive, that if you hotplug it in, odds are the uhci_hcd would be used, thus bringing it to USB 1.1 speeds, but if you reboot and keep it plugged in during startup, that it would be recognized properly. 

I have a greater feeling that it's the latter that actually solved my problem, but being on the newer kernel couldn't hurt I guess :P

---

