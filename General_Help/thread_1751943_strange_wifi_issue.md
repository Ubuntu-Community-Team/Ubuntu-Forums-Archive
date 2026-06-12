---
title: "strange wifi issue"
date: 2011-05-07
forum: General Help
---

### Post by pabc on 2011-05-07
short question: why do I need to 
```
modprobe ath5k
```

or add 'ath5k' it to /etc/modules in order to get wifi working since i cocked about trying to get my wifi up and running?


background:
I was running my acer aspire one zg5 on 10.04 but the wifi always dropped under heavy traffic - ie moving a video to a local folder from a NAS drive.

I tried ndiswrapper / winxp drivers and although it solved the drops it was a little flaky and produced random restarts.

madwifi compiled from source worked better but still dropped.

in my cocking about i managed to lose wifi altogether so did a dist upgrade to 10.10 hoping that would fix it (live 10.10 and 11.04 worked fine under heavy traffic) but it was still missing from network manager until i forced the loading of ath5k. why doesn't it just work as before. what have i changed that i've forgotten to change back? I never used to force it load with an addition to modules or a modprobe call

---

