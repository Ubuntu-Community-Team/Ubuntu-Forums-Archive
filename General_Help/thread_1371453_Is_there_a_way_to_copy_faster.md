---
title: "Is there a way to copy faster?"
date: 2010-01-03
forum: General Help
---

### Post by MindFusion on 2010-01-03
Hi everyone,

I decided to put my music collection of 8 gigs off my iPod onto my Ubuntu desktop, but when i dragged the files onto my Music folder, the estimated copying time was 3hours and 45 minutes...

I waited the entire time and now they are finally copied, but i can't remember ever having to wait that long to copy files... Is there a way to make copying go faster? Without having to wait an hour every 2 gigs copied?

---

### Post by NFblaze on 2010-01-03
I wonder this too. I think there is a slow down between fat to ext. Although, you could always try rsync

---

### Post by andyba on 2010-01-05
I have the same problem, and yes I think this is a problem. Waiting 2 hours to copy 3 GB of files is not acceptable on a quad core with 8 GB of RAM.
Are there any solutions to this problem?

---

### Post by MindFusion on 2010-01-18
*bumps*

---

### Post by Lekensteyn on 2010-01-18
Copying in ubuntu has always been very fast for me.

Maybe a stupid answer, but have you connected it with USB 2.0?

---

### Post by philinux on 2010-01-18
> **MindFusion said:**
> Hi everyone,

I decided to put my music collection of 8 gigs off my iPod onto my Ubuntu desktop, but when i dragged the files onto my Music folder, the estimated copying time was 3hours and 45 minutes...

I waited the entire time and now they are finally copied, but i can't remember ever having to wait that long to copy files... Is there a way to make copying go faster? Without having to wait an hour every 2 gigs copied?

You could try using the cp command instaed of nautilus. Or use another file manager like thunar.

---

### Post by tgalati4 on 2010-01-18
man rsync

---

### Post by Grenage on 2010-01-18
USB speed is, and has been shockingly bad for me - at least most of the time.  I think it's connecting at USB1 speed, seemingly connecting at USB2 about 1/10 times.  I think I recall someone posting logs showing that it was negotiating USB1.

I've never got around it.

---

### Post by nothingspecial on 2010-01-18
Both cp and nautilus told me it would take about 5 days to copy my 450 gig music collection.

pcmanfm did it in a few hours.

Can`t explain why.

---

### Post by J V on 2010-01-18
man hdparm - you can make your HD up to 20 times faster, all extras are disabled by default for stability, but some people like speed :P

---

### Post by argosreality on 2010-01-18
That does seem rather slow (35kb/s?) which is slower than even USB1 should transfer at. USB2 you'll max out typically around 20-30Mb/s on a good drive (best I've seen under Ubuntu was 10-15).

Having said that the drive in an iPod is typically a much slower drive but still...far far faster than what you got.

---

### Post by MindFusion on 2010-01-20
Well yeah, I second that, iPod is the fastest USB device I have, it can copy a 4 gig music collection in just 5 minutes, the problem rather is unpacking it when transferring it again to your computer...

---

