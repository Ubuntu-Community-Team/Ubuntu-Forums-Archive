---
title: "Inconsistent Detection of mobile broadband dongle"
date: 2012-09-10
forum: General Help
---

### Post by RationalAsh on 2012-09-10
Ok, here's the problem. My mobile broadband dongle is only sometimes detected. It's a Huawei EC1561 dongle. I've read a load of other threads about these dongles but all in all of them the modem is either not detected or detected.

I've already installed USB modeswitch. I have wvdial but I don't use it or need it because the Ubuntu network manager can connect me to the internet using the modem without any problems. (In fact it works better than in windows. Faster too I think.)

**The problem is that the dongle is only detected if I boot into windows first with the modem inserted, then restart and boot into ubuntu with the modem still inserted. If shutdown and boot directly into ubuntu the modem is not detected. The option to connect through mobile broadband does not appear in the network manager.**

There was a thread which suggested that I should try clicking the safely remove hardware option from within ubuntu to try and get it to be detected but the problem is that ubuntu never detects it as a storage device (I think) even when I can connect using it. 

The output  of lsusb is always the same. I can see the huawei datacard/modem in the list. But no storage device turns up at all.

So now I'm forced to boot windows first and restart then boot into ubuntu everytime I want to use the internet in ubuntu.

Any idea what might be wrong here?

---

