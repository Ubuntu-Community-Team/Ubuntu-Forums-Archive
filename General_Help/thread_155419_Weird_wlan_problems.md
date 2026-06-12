---
title: "Weird wlan problems"
date: 2006-04-05
forum: General Help
---

### Post by Kashirigi on 2006-04-05
Hi,

I'm relatively new to linux, and everything was sailing along smoothly. However, in the past couple of days something has me banging my head.

I'm using my Broadcomm (linksys) wireless card to connect to the internet. It was running perfectly, using ndiswrapper and wpa_supplicant. Everything would go smoothly at boot, and life was happy.

Now, however, on boot things seem to go wrong. ndiswrapper et al are still being loaded, but I have no connectivity. When I try to actually use my connection (say, by using firefox), my entire machine will hang. No CTRL-ALT-Backspace, no nothing, no switching to other terminals. Just dead.

However, if before I start any sort of network activity, if I ifdown wlan0 and ifup wlan0 everything is fine.

I have no idea where to start looking for the problem, because I haven't actually changed anything for weeks (besides plugging in a different keyboard).

If anyone could give me any ideas where to start, I would be thankful.

---

### Post by Kashirigi on 2006-04-05
Oh my god. I've been banging my head for days and five minutes after I post I find the solution.

In the GNOME networking administration, the DNS servers were set to something completely arbitrary. I have no idea where these values came from, because previous to five minutes ago I had never even looked there. When I changed them to my *correct* DNS servers and rebooted, everything started working fine again.

](*,) 


Well, if anyone can shed light on my horrendous crashes, please let me know.

---

