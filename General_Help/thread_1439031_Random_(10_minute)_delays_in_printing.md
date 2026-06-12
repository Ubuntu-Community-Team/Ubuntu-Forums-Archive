---
title: "Random (10 minute) delays in printing?"
date: 2010-03-25
forum: General Help
---

### Post by thorpflyer on 2010-03-25
Hi all,

I have recently installed Ubutnu 9.10 on  a laptop machine for my girlfriend, and she uses an HP 6300 series all-in-one printer. While things are generally good, the printer randomly delays output for long periods, often as much as ten minutes of delay. The delays might occur at any point during the output, that is, printing will often start, but then hang part way through a page. Sometimes, the delay is sol long (more than ten minutes) that the printer seems to timeout, form feeds the page, and abandons the output. Mostly, however, great patience results in output resuming after the many minutes delay and the page will complete. For multi-page outputs, the delay might occur more than once during the total output, and sometimes you get lucky and the whole thing comes out in a single shot.

Anyone seen this before? Any ideas what might be happening, and what to do about it? Needless to say, my girlfriend is eying up the windows xp install disks and expressing socially unacceptable desires :(

TIA
Simon

---

### Post by thorpflyer on 2010-03-26
Hmm, while trying to work out why the machine that's having this printing problem was cranking it's CPU fan continuously, I discovered that the syslog daemon was running at about 50% CPU usage. This led me to the log files. So far, in about 12 hours since original build, I have some 5GB of logs already. Ho hum, something's unhappy. Sure enough, it's something to do with the printer. These are the messages, repeated ad infinitum:

daemon.log:
Mar 26 14:39:40 christine-laptop hp[1148]: io/hpmud/musb.c 1022: bulk_write failed buf=0xbf7fc3b4 size=7680 len=-16: Device or resource busy
Mar 26 14:39:40 christine-laptop hp[1148]: io/hpmud/musb.c 1389: unable to write data hp:/usb/Officejet_6300_series?serial=CN73KCF0TH04J5: Device or resource busy
Mar 26 14:39:40 christine-laptop hp[1148]: io/hpmud/musb.c 725: invalid deviceid wIndex=1, retrying wIndex=100: Device or resource busy
[... repeat until disk fills up ;> ...]

messages, kern.log, and syslog:
Mar 26 14:39:40 christine-laptop kernel: [  304.438569] usb 1-2: usbfs: process 1148 (hp) did not claim interface 1 before use
[... also repeat forever ...]

Note that during this output, the printing continues from time to time, so the error is not permanent/fatal.

Can anyone offer any pointers now? It'd be great to make this system work properly!

Cheers,
Simon

---

### Post by thorpflyer on 2010-03-26
Well, this seems to be a known bug--something to do with the USB subsystem as much as with hplip, though I'm not entirely sure I understood the writeup, and more importantly I've not been able to find a workaround or fix.

I've worked around it by the rather unsavory approach of attaching the printer to my girlfriends windows desktop system and driving the printer through the network instead of through the USB port.

The point of the exercise, of course, is to remove windows entirely from the house, but that's proving more difficult than I'd hoped, still.

---

