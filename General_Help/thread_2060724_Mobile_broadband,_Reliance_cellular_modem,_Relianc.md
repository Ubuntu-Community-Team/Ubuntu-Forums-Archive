---
title: "Mobile broadband, Reliance cellular modem, Reliance India"
date: 2012-09-20
forum: General Help
---

### Post by Advait on 2012-09-20
Hi All,

I live in India and use a Reliance cellular mobile broadband usb modem for my internet. On version 10.10 it worked fine; connected every time and did not need to edit wvdial.conf.

On versions 11.04 to 12.04 it doesn't work. I've tried editing the wvdial.conf file and it still doesn't work. I've had some good Linux techies look at it and they could not get it working.

Any ideas on what changed from 10.10 to the more recent versions that would cause a cellular mobile broadband usb modem not to work? I'd love to get it working on 12.04. All my usb-modeswitch files are installed and up to date.

Thanks,

Advait

---

### Post by Advait on 2012-09-21
OK, I finally got it solved. The solution was very non-obvious and was found by accident. Ubuntu is wonderful but tasks that take me seconds in Windows can take hours or days in Ubuntu. Oh well, welcome to open source... DIY...

---

### Post by newb85 on 2012-09-22
Why not post your solution so that the next person doesn't have to DIY?

---

### Post by Advait on 2012-09-23
> **newb85 said:**
> Why not post your solution so that the next person doesn't have to DIY?

Good suggestion. Thanks! Here's the overview of how I fixed it.

Background: For about 2 years I used the Reliance mobile broadband usb cdma cellular modem with Ubuntu 10.10 and it worked fine. I didn't need to edit wvdial.conf or anything like that. I just went into network settings and created a profile for the Reliance modem, and entered in the user name and password. To connect I clicked on the "antenna" icon on the upper right hand side which displays the available network connections. I'll call it the Network Connections Icon or "NCI" for short. Then (if needed) I clicked on "enable mobile broadband" and then clicked on Reliance. The NCI did it's little broadcasting animation and then the signal strength bars icon ("SSBI") would appear indicating a successful connection.

So the key point here is that it got drilled into my mind that I HAD to use the NCI to create a cellular broadband connection. This mindset was the source of my problems when I recently upgraded to 12.04. Details below...

So in 12.04 I used the same steps as in 10.10 (and as described above). It only worked 1 time out of ten. Grrr! Then a friend said "Edit the wvdial.conf file." I did and it still only worked 1 time out of ten. My friend then said "Run "sudo wvdial" and see if that works." Then I executed "sudo wvdial" and then clicked on the NCI. But clicking on Reliance never worked. Grrr! Running wvdial would come back with DNS and network addresses, so obviously it was connecting, but clicking on Reliance under the NCI never worked (it never went to the SSBI). The broadcast animation would run for a few seconds and then it displayed the message "modem disconnected". Grrr!

Then (purely by accident) I ran sudo wvdial and then clicked on the FireFox icon. It connected! My home page appeared. Wow! I was totally convinced that I *needed* to see the SSBI to get a connection. Not true! So the solution was to simply IGNORE the NCI.

To most of you experienced Linux people, this solution is probably blindingly obvious, but to a newbie like me it wasn't. So hopefully this may help other Reliance and Linux users in India to avoid the problems I had.

Hope this helps! Cheers,

Advait

---

