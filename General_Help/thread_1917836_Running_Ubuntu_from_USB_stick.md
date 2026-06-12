---
title: "Running Ubuntu from USB stick"
date: 2012-01-30
forum: General Help
---

### Post by MacUsers on 2012-01-30
Dear all,

Is any one running/booting Ubuntu (11.10 server) from USB stick? I know booting gonna be slower, which I don't care too much about it. My concern is with "suspend to disk" operation - is it gonna work okay due to the low write speed compare to the normal HDD? cheers!!

---

### Post by Double.J on 2012-01-30
Hi there, 

In my experience of using a live USB with persistence, sleep works fine, hibernate doesn't work - no swap space available :)

Another observation - if you always use the stick on the same machines, consider an install to USB over live USB - as you start to fill up the persistence file boot times start to get silly (esp if you rack up a  couple of G's) Also not using a compressed filesystem helps - the only downside is that you need an 8GB stick upwards - not really a cost issue anymore (I got 16GB for a tenner in the sales) but if you don't want to buy a new stick may affect your decision?


Hope it helps :)

---

### Post by MacUsers on 2012-01-30
Yes, I'm planning a 16G USB stick and not using Live USB as well. I installed Ubuntu directly onto the USB stick, which took awful lot of time but eventually finished and worked. Considering the fact that I do have swap space on the USB stick, how well hibernate will work you think (I'm using it in HP N40L MicroServer; S3 is not supported there)? 

On a separate note, do you have recommendation for a suitable USB stick? Cheers!!

---

