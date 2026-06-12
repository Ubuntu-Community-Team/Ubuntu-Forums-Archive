---
title: "Transmission Web Interface only works on localhost"
date: 2009-07-27
forum: General Help
---

### Post by alek66 on 2009-07-27
Hi everyone, I installed Trans on my linux head-less box, so is pretty handy to have web interface. It used to worked fine! All of the sudden, the web interface accesed from my Mac is blank
[[IMG]http://img253.imageshack.us/img253/2103/mac.th.tif[/IMG]](http://img253.imageshack.us/i/mac.tif/)
But on the linux box shows everything.

[[IMG]http://img252.imageshack.us/img252/9932/linux.th.tif[/IMG]](http://img252.imageshack.us/i/linux.tif/)I check transmission prefs... there is no acces user, and no IP blocked.

---

### Post by aloshbennett on 2009-07-27
This sounds lame, but have you tried looking at the source of the blank html page to make sure its really blank?

---

### Post by alek66 on 2009-07-28
HTML shows nothing.... that can tell me that refers that is not blank...

anyone help?

---

### Post by DaithiF on 2009-07-28
From your screenshot, you're not actually getting a 'blank' page, you're getting a transmission webpage that shows 0 items being uploaded/downloaded.

Theres a big difference between those two -- a truly 'blank' response could be a connection / firewall issue between your machines, whereas the fact that you are actually getting a response (albeit with the incorrect content) tends to rule out that possibliity.

I've seen reports before of Safari on Macs not loading html correctly from Transmission (e.g. see [http://forum.transmissionbt.com/viewtopic.php?f=8&t=3862&start=0 )]("http://forum.transmissionbt.com/viewtopic.php?f=8&t=3862&start=0")
One suggestion there was to try Firefox on the Mac instead, which seemed to work.

good luck
d

---

### Post by alek66 on 2009-07-28
DaithiF

thanks for the tip, ill read into that forum. It used to worked, so thats why i posted.

Thanks!

---

