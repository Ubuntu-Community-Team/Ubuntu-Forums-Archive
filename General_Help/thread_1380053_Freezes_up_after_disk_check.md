---
title: "Freezes up after disk check"
date: 2010-01-13
forum: General Help
---

### Post by oxf on 2010-01-13
My laptop keeps freezing after the routine disk check completes, along with a screen of jiggly colours. I also booted into safe mode and ran the  disk check from there with the same result. 

Any ideas on how to proceed? What more info do you need?

Thanks

---

### Post by patros on 2010-01-13
"jiggly colours"? try running the memtest option from the grub screen

---

### Post by oxf on 2010-01-13
> **patros said:**
> "jiggly colours"? try running the memtest option from the grub screen

By jiggly I mean there are bands of colours across the screen like the display's not properly loaded or something. Actually I normally get these anyway on boot up but it just for a fraction of a second during the boot process.

I'll try the memtest

---

### Post by patros on 2010-01-13
Maybe it hasn't frozen, maybe your graphics card isn't being detected properly. Try hitting CTRL+ALT+F5 when it happens, should take you to a console. If it doesn't leave it for a minute to make sure and try it again.

---

### Post by oxf on 2010-01-13
Well I tried the memtest from the Grub screen and it did list a couple of errors. I ran it several times and the errors came up at the same mem address each time. I don't know what this means for my system as I've never ran the memtest before (faulty RAM?) and have noticed any memory related problems, not say there couldn't be some. Also how is this related to my pc freezing after the diskcheck?

---

### Post by oxf on 2010-01-13
Is there a way of running the disk scan from within the desktop rather than having to wait for the number of boot ups to trigger it?

Thanks

---

### Post by patros on 2010-01-13
Faulty ram can cause all types of problems. One of those problems is if data is stored to ram before being written to disk the data can be corrupted. I wouldn't use your computer until you have replaced the faulty ram. How much ram have you got? You might get lucky, if you have 2 x 1Gb ram chips try taking one out and rerun the memtest. If it still has errors swap them and run the memtest again. Have you any experience removing/installing ram?

---

### Post by oxf on 2010-01-13
> **patros said:**
> Faulty ram can cause all types of problems. One of those problems is if data is stored to ram before being written to disk the data can be corrupted. I wouldn't use your computer until you have replaced the faulty ram. How much ram have you got? You might get lucky, if you have 2 x 1Gb ram chips try taking one out and rerun the memtest. If it still has errors swap them and run the memtest again. Have you any experience removing/installing ram?

Yes this laptop came with 2 X 256MB which I removed and installed 2 X 512.   
1GB is the  max it can take. I try pulling them out tomorow

---

