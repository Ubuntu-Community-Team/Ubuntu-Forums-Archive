---
title: "Another Suspend Thread"
date: 2012-08-22
forum: General Help
---

### Post by not so there on 2012-08-22
Since installing 12.04 I have been unable to use the suspend function. I am also unable to use it with the live cd. 

The computer suspends but upon waking up it will nothing will appear on either monitor even though the machine sounds like it is on. I am unable to remote connect to it at this point and must hard reset.

I have used both the 3.2 and the 3.4 kernel and I still have the problem. (I updated since I was having lock ups in unity and it is now much less often).

The /var/log/pm-suspend.log looks fine from what I can tell, no errors.

I have used the scripts in the threads [http://ubuntuforums.org/showthread.php?t=1978290](http://ubuntuforums.org/showthread.php?t=1978290)
and
[http://ubuntuforums.org/showpost.php?p=11186249&postcount=6](http://ubuntuforums.org/showpost.php?p=11186249&postcount=6) without success.

I disabled the USB3.0 in the bios.

I have no problems with suspend in windows 7.

Using a ga-z68xp-ud3 motherboard and a ATI 6950.

---

### Post by not so there on 2012-08-27
I was able to figure out that my suspend issue was caused by the presence of my ATI Radeon HD 6950. If I removed the card and used the on board video then suspend would work perfectly. 

I tried installing the ATI drives through Ubuntu and the ones available from ATI directly and still had the same issues with suspend failing. 

I was able to get everything working correctly by using the updated open source drives and 3.5 kernel available from the xorg-edgers ppa. [http://www.ubuntuupdates.org/ppa/xorg-edgers](http://www.ubuntuupdates.org/ppa/xorg-edgers)

---

