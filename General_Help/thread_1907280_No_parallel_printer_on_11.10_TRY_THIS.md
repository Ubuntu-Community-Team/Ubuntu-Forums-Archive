---
title: "No parallel printer on 11.10 TRY THIS"
date: 2012-01-11
forum: General Help
---

### Post by sanddgroper on 2012-01-11
Having installed Ubuntu 11.10 I went to add the printer,my trusty BJC 1000SP,but to my surprise it would not print.A bit of trouble shooting seemed to show that there was no selection for a parallel printer.So I had a look back at one of my old Ubuntu installations and found that the URI for that system was "parallel:/dev/lp0"(thats zero not OH).So I added that line to my device URI setting in my printer settings for 11.10 and low and behold off it went looking for a driver for my BJC 1000SP.the closest it came was the driver for a BJC 1000 but this was good enough.
So if you are having a problem getting your parallel printer to work TRY THIS
parallel:/dev/lp0 in the device URI setting

Cheers
sanddgroper

---

