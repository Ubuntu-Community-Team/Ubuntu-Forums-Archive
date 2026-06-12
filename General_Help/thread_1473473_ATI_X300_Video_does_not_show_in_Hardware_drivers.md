---
title: "ATI X300 Video does not show in Hardware drivers"
date: 2010-05-05
forum: General Help
---

### Post by joelw135 on 2010-05-05
How do I get my X300 ATI PCIE card to show in Hardware Drivers so the driver will work? I installed the drivers from the Ubuntu software Center. I am using Ubuntu 10.4.

---

### Post by StuartN on 2010-05-05
> **joelw135 said:**
> How do I get my X300 ATI PCIE card to show in Hardware Drivers so the driver will work? I installed the drivers from the Ubuntu software Center. I am using Ubuntu 10.4.

You are already using the available open source driver. The x300 is a legacy device and no longer supported by the ATI Radeon proprietary driver [http://support.amd.com/us/gpudownload/windows/Legacy/Pages/radeonaiw_vista32.aspx](http://support.amd.com/us/gpudownload/windows/Legacy/Pages/radeonaiw_vista32.aspx)

---

### Post by joelw135 on 2010-05-05
> **StuartN said:**
> You are already using the available open source driver. The x300 is a legacy device and no longer supported by the ATI Radeon proprietary driver [http://support.amd.com/us/gpudownload/windows/Legacy/Pages/radeonaiw_vista32.aspx](http://support.amd.com/us/gpudownload/windows/Legacy/Pages/radeonaiw_vista32.aspx)

I am unable to turn on any desktop effects, it says no compatible hardware found.

---

### Post by dino99 on 2010-05-05
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by StuartN on 2010-05-05
> **joelw135 said:**
> I am unable to turn on any desktop effects, it says no compatible hardware found.

I do not know what features the open source driver has for your card. It became an issue in Ubuntu 9.04 with a change in Xorg at the same time as ATI Radeon dropped support for the legacy cards such as X300.

[http://ubuntuforums.org/showthread.php?t=1134991](http://ubuntuforums.org/showthread.php?t=1134991)

---

### Post by joelw135 on 2010-05-05
> **StuartN said:**
> I do not know what features the open source driver has for your card. It became an issue in Ubuntu 9.04 with a change in Xorg at the same time as ATI Radeon dropped support for the legacy cards such as X300.

[http://ubuntuforums.org/showthread.php?t=1134991](http://ubuntuforums.org/showthread.php?t=1134991)

Well I just had to re-install Ubuntu. I screwed up and installed the X-conf driver and I got a screwed up screen. I then tried to remove it and no dice. I re-installed and for some strange reason effects are now working. At least the normal ones are. I will leave well enough alone and be happy with what I have until I find a inexpensive PCIE card that works with Ubuntu. I have no idea what works and what cards will not work.

---

### Post by dino99 on 2010-05-05
your card might work, lot of users around with it working smootly

---

### Post by joelw135 on 2010-05-05
> **dino99 said:**
> your card might work, lot of users around with it working smootly

I am going to stick with it now that it is working. But Since this is the first install where it is working, I suspect it won't be shortly. I have installed 10.4 three times and this is the first one where the effects work.

---

