---
title: "Mouse randomly freeze"
date: 2011-01-16
forum: General Help
---

### Post by Ginosal on 2011-01-16
Hi. I've just upgraded from 10.4 to 10.10. After the upgrade, my mouse keeps freezing for some milliseconds every 10-15 seconds. I know that the issue has already been posted, but those are different distros, kernels, versions and, for one reason or another, those solutions could not be applied to my issue...

This problem comes up only when I use the latest kernels (2.6.35-xx), but when I load (from grub) the older one (2.6.32-27), my mouse works perfectly.

Maybe this can help: when I use 2.6.35-xx and my mouse keeps hanging, i get this messages in "message" log:

```
Jan 16 12:12:52 desktop kernel: [   22.451602] radeon 0000:01:05.0: HDMI Type A-1: EDID invalid.
Jan 16 12:12:52 desktop kernel: [   22.503813] 
Jan 16 12:12:52 desktop kernel: [   22.553518] 
Jan 16 12:12:52 desktop kernel: [   22.603825] 
Jan 16 12:12:52 desktop kernel: [   22.653534] 
Jan 16 12:12:52 desktop kernel: [   22.653537] radeon 0000:01:05.0: HDMI Type A-1: EDID invalid.
Jan 16 12:12:52 desktop kernel: [   22.941415] 
Jan 16 12:12:52 desktop kernel: [   22.991116] 
Jan 16 12:12:52 desktop kernel: [   23.040813] 
Jan 16 12:12:52 desktop kernel: [   23.090507] 
Jan 16 12:12:52 desktop kernel: [   23.090509] radeon 0000:01:05.0: HDMI Type A-1: EDID invalid.
Jan 16 12:12:52 desktop kernel: [   23.141893] 
Jan 16 12:12:52 desktop kernel: [   23.191599] 
Jan 16 12:12:52 desktop kernel: [   23.241286] 
Jan 16 12:12:52 desktop kernel: [   23.290969] 
Jan 16 12:12:52 desktop kernel: [   23.290970] radeon 0000:01:05.0: HDMI Type A-1: EDID invalid.
Jan 16 12:12:53 desktop kernel: [   23.571394] 
Jan 16 12:12:53 desktop kernel: [   23.621096] 
Jan 16 12:12:53 desktop kernel: [   23.670781] 
Jan 16 12:12:53 desktop kernel: [   23.720486] 
Jan 16 12:12:53 desktop kernel: [   23.720488] radeon 0000:01:05.0: HDMI Type A-1: EDID invalid.
Jan 16 12:12:53 desktop kernel: [   23.771872] 
Jan 16 12:12:53 desktop kernel: [   23.821578] 
Jan 16 12:12:53 desktop kernel: [   23.871261] 
Jan 16 12:12:53 desktop kernel: [   23.920951] 
Jan 16 12:12:53 desktop kernel: [   23.920952] radeon 0000:01:05.0: HDMI Type A-1: EDID invalid.
```

This doesn't happen when I use the older kernel. My log is perfectly clean. How can I use the latest kernels without this issue?

Well, sorry for my poor english. Thank you in advance!

---

