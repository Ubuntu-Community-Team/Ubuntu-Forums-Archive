---
title: "Direct Rendering with a Radeon x600"
date: 2011-10-15
forum: General Help
---

### Post by jeremyh on 2011-10-15
I have a laptop with a radeon x600 and while the performance seems okay, I do not have direct rendering. I would like to get compiz working so I can use Avant Window Manager. 

I tried installing the closed source fglrx driver but it says that it can't find a supported adapter. 

Thanks, 
Jeremy Harmon

---

### Post by jeremyh on 2011-10-15
Not sure exactly how but I got it working. I followed the directions at [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch) to get rid of fglrx, and now I have direct rendering support and compiz is working.

---

