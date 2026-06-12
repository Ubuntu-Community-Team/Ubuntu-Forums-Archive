---
title: "WiFi Internet Issues"
date: 2011-06-28
forum: General Help
---

### Post by steevven1 on 2011-06-28
So, I'm having some trouble with my WiFi connection: Its speed and connection comes in bursts. For example, it will take 5-10 seconds in Firefox saying "connecting," and then all at once the entire page will load instantaneously, etc. I get disconnected and reconnected to a wireless network that has a great signal for no apparent reason, especially when running on battery it seems, but maybe that part is just my imagination or coincidence.

I am 99% sure that this is a problem with my wireless card driver, but there is some chance that it's not. I'm running Ubuntu 11.04 64-bit on a Lenovo ThinkPad X220 with a Realtek RTL8188CE 802.11b/g/n WiFi Adapter. I manually compiled and installed the official Linux drivers from Realtek's website (the ones that came with Ubuntu were nearly unusable he connection was so bad).

**My questions are:** 
1) In the event that maybe it isn't my driver's fault, what other things could be causing this problem? Anything else worth checking?
2) Is it worth trying to install the Windows driver using ndiswrapper? How do I do this? I've never tried it before.

THANK YOU!

---

### Post by steevven1 on 2011-06-28
Interesting update, though I'm not sure it's of any consequence: It appears that if I continually keep requesting data through the network, I never get disconnected, and my speeds improve. I have left "ping google.com" running in my terminal for a while, and my problems are apparently solved.

Obviously, this is not the permanent solution I want to use, but maybe it sheds light on the root of the problem.

I can say this for sure: It has NOTHING to do with the network I am connected to. No other computers experience similar issues on the same networks, and it pervades multiple networks. I'm still convinced it's a WiFi driver issue for now.

---

### Post by AudiCross on 2011-09-01
Were you able to find a solution to this problem? I have a lenovo x120e with the same wireless adapter and the exact same issue. So far I have not been able to solve this. Your help would be greatly appreciated.

---

### Post by Pariah819 on 2011-09-10
I would suggest that you follow the driver installation provided by [wildmanne39]("http://ubuntuforums.org/member.php?u=508533") in the post below...

[http://ubuntuforums.org/showpost.php?p=11102146&postcount=6](http://ubuntuforums.org/showpost.php?p=11102146&postcount=6)

---

