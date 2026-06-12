---
title: "Very Slow Write Speeds to USB External Hard Drive"
date: 2010-10-11
forum: General Help
---

### Post by eArquilla on 2010-10-11
I'm trying to back up my hard drive to a 2 TB WD external so that I can do a clean install of 10.10, however I'm getting tremendously slow write speeds. It hovers around 1.5 MB/s and steadily slows from there. It tells me it will take 150+ hours to transfer 400 GB of data.

I have a AMD quad core processor and 8 gigs of ddr3 ram... USB 2.0... I feel this should go much faster.

---

### Post by QIII on 2010-10-11
Yes.  It should go much faster.  There has been much wailing and gnashing of teeth over this in the past.

Are you powering your drive from the USB bus or from a dedicated power supply?

Do you have any other USB devices sharing the bus?

---

### Post by lisati on 2010-10-11
That does seem rather slow.  Others might be able to offer insight that is more helpful, but the best thing that comes to mind for me at the moment is to wonder how full the external HDD is. I noticed with a couple of external HDDs I have that as they filled, writing to them seemed to slow down.

---

### Post by TimEnid on 2010-10-11
are you doing drag and drop? I find that using grsync is much more reliable.

---

### Post by eArquilla on 2010-10-11
It is a 2Tb hard drive and I have about 500 gigs filled, so it still has plenty of room. It is directly plugged into an outlet. I'll look into grsync, never heard of it before.

Thank you all for your replies, and if anybody has anything else to add it would be very appreciated!

---

### Post by QIII on 2010-10-11
There's a lot of bickering over this, including the "Linux sucks and can't do this!" crowd.  Windows 7 forums are full of this problem, too.

There are about three schools of thought on this.

1.  The problem is caused by powering the device from the USB bus.  You've eliminated this one.

2.  Multiple USB devices connected to the bus change the voltage, and your system thinks it should be set to USB 1.1 because of that.  I have my doubts.  But worth a try removing what you can to see.

3.  The problem is caused by legacy USB support for 1.1 being enabled in your BIOS.

---

