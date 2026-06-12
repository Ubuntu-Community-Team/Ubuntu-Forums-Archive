---
title: "What to do when Jaunty does not support you?"
date: 2009-10-18
forum: General Help
---

### Post by KayakJim on 2009-10-18
I have 3 laptops that have ATI video cards that are not supported by Jaunty. As such, they are still running Intrepid.

Can anyone advise what possible options I have to be able to run a current Linux OS, either with Ubuntu or another distribution?

I find it surprising that I am in this situation since Linux started with the whole premise of being able to run on older equipment. :/

---

### Post by darkstaar on 2009-10-18
You didn't mention whether or not you've tried the open source ATI drivers. My laptop uses an ATI 'legacy' adapter as well but runs fine with the open source drivers under Jaunty.

---

### Post by KayakJim on 2009-10-18
> **darkstaar said:**
> You didn't mention whether or not you've tried the open source ATI drivers. My laptop uses an ATI 'legacy' adapter as well but runs fine with the open source drivers under Jaunty.

I have not tried ATI's open source drivers. The last time I tried Jaunty was shortly after it was released and the ATI drivers were not compatible.

Thank you for the information and I will give them a try and hopefully everything will work well.

---

### Post by darkstaar on 2009-10-18
Try [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) for more info.

---

### Post by mcduck on 2009-10-18
> **KayakJim said:**
> I have 3 laptops that have ATI video cards that are not supported by Jaunty. As such, they are still running Intrepid.

Can anyone advise what possible options I have to be able to run a current Linux OS, either with Ubuntu or another distribution?

I find it surprising that I am in this situation since Linux started with the whole premise of being able to run on older equipment. :/

I'm not aware of any Ati card that wouldn't be compatible with Ubuntu.

With the latest cards (using R600 or R700 series GPUs) you'll want to use Ati's proprietary fglrx drivers.

For all the others (R100&#8211;R600 series GPUs) Ubuntu provides you by default with open-source driver that has at least some level of 3D acceleration support. These cards are nt supported by Ati's proprietary drivers any more, so you get the best possible driver by default.

Note that if you try to upgrade a system that still runs Ubuntu version which had old enough version of fglrx drivers to support your graphics card (other than the R600 or R700), the upgrade process won't be able to automatically switch you into using the open-source driver. In those cases you'd better just do a fresh install. This would be the case when upgrading from 8.10 or older version to 9.04 or later.

*****

So, if you make a fresh install of 9.04 or later, these are your options:

- For Ati card with R100 &#8211; R600 series GPU, you don't need to do anything. The default install gives you the best driver you are going to get.

- For cards with R700 or later GPU use the restricted drivers tool in System/Administration-menu to install Ati's proprietary fglrx drivers.

---

### Post by KayakJim on 2009-10-18
Two of the laptops have ATI X300 cards. I will have to check on the third one as I do not recall what it has at the moment.

My newest laptop has an ATI 4650HD but I am waiting for 9.10 on that system.

---

### Post by mcduck on 2009-10-19
> **KayakJim said:**
> Two of the laptops have ATI X300 cards. I will have to check on the third one as I do not recall what it has at the moment.

My newest laptop has an ATI 4650HD but I am waiting for 9.10 on that system.

X300 is supported by the opensource radeon driver (which Ubuntu uses by default), and HD4650 should work just fine with Ati's fglrx driver.

---

### Post by KayakJim on 2009-10-19
> **mcduck said:**
> X300 is supported by the opensource radeon driver (which Ubuntu uses by default), and HD4650 should work just fine with Ati's fglrx driver.

Great!  Thank you very much.

---

