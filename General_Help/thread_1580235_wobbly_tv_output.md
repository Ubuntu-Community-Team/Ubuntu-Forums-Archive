---
title: "wobbly tv output"
date: 2010-09-23
forum: General Help
---

### Post by Gorlist on 2010-09-23
Hi, im running ubuntu 10.04 on a Acer TravelMate 5520, ATI Xpress 1250. The Sony 40" TV is connected to the laptop with a VGA plug, but with 10.04 im finding the output picture is wobbly, distorted regardless of resolution.

It does work fine on ubuntu 9.04, picture perfect. Ive booted into both and checked the resolution and their identical.

Any suggestions? 

Best Regards

---

### Post by robsoles on 2010-09-29
Did you check the refresh rate being used by each version?

---

### Post by Gorlist on 2010-09-29
Hi, sorry for the slow reply, ive been away for the weekend. Yes both set to 60Hz.

---

### Post by robsoles on 2010-09-29
And both report using 60Hz for the TV when it is hooked up?

---

### Post by Gorlist on 2010-09-30
Yes I believe so, I will double check however.

---

### Post by Gorlist on 2010-09-30
Just checked, and can confirm TV is using 60hz.

---

### Post by Grenage on 2010-09-30
Since it worked fine in 9.10, we can rule out hardware and cable length.  Have you tried alternative drivers?

---

### Post by Gorlist on 2010-09-30
How would I do so? using the default ubuntu open source drivers for the ATI Xpress 1250.

---

### Post by robsoles on 2010-09-30
Synaptic package manager may include alternative drivers but identifying them may not be easy. Maybe [http://www2.ati.com/drivers/linux/linux_8.30.3.html](http://www2.ati.com/drivers/linux/linux_8.30.3.html) has a usable driver listed or refers to where you might find one. [www.google.com/search?q=ati+Xpress+1250+linux+driver](www.google.com/search?q=ati+Xpress+1250+linux+driver) may help too.

---

### Post by Grenage on 2010-10-01
Do you get the option of proprietary drivers, under Advanced/Hardware Drivers?

---

### Post by Gorlist on 2010-10-01
> **Grenage said:**
> Do you get the option of proprietary drivers, under Advanced/Hardware Drivers?

No, ATI stopped supporting the latest kernal's since 9.04? 

Thanks robsoles, will take a look later on today.

---

### Post by Grenage on 2010-10-01
> **Gorlist said:**
> No, ATI stopped supporting the latest kernal's since 9.04? 

Thanks robsoles, will take a look later on today.

Ah I see; I haven't used ATI in a long time, due to poor Linux support.

---

### Post by Gorlist on 2010-10-12
This problem seems to have been resolved since updating to 10.10. Thanks for help!

---

