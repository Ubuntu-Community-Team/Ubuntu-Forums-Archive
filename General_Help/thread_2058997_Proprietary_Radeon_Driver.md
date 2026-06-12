---
title: "Proprietary Radeon Driver"
date: 2012-09-17
forum: General Help
---

### Post by jandalf on 2012-09-17
Hello everyone,

I have installed the proprietary ATI Radeon driver and now when I restart the computer when Ubuntu starts loading the screen turns off and doesn't come back on, how can I fix this?

---

### Post by dcstar on 2012-09-17
> **jandalf said:**
> Hello everyone,

I have installed the proprietary ATI Radeon driver and now when I restart the computer when Ubuntu starts loading the screen turns off and doesn't come back on, how can I fix this?

If you have an additional HDMI output connected then unplug it, chances are the video settings need to be configured by the AMD Catalyst tool to use the connection you have your monitor plugged into.

---

### Post by mastablasta on 2012-09-17
what card do you have?

---

### Post by jandalf on 2012-09-17
I have a 4870 ATI Radeon card.

There is a hdmi output however nothing is plugged in, sounds like a likely reason although i'm not sure how to go about configuring the ATI catalyst. Thanks for all help.

---

### Post by jandalf on 2012-09-19
bump

---

### Post by Mark Phelps on 2012-09-19
Try using the info in the link below to REMOVE the ATI drivers and replace them with the open-source Radeon driver:

[https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection?action=show&redirect=X%2FTroubleshooting%2FFglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch]("https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection?action=show&redirect=X%2FTroubleshooting%2FFglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch")

---

