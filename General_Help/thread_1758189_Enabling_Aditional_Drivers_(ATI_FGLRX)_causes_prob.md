---
title: "Enabling Aditional Drivers (ATI FGLRX) causes problems"
date: 2011-05-14
forum: General Help
---

### Post by aryzing on 2011-05-14
Hi, 

I have an Asus 1215b with 11.04 on it. I chose to investigate whether the video performance would inclrease if I enabled the Additional Drivers for it (propriety drivers).

Having done this has increased video performance, but it has also brought with it two unwanted effects:

1. The terminal reslution has changed (when you press Ctrl+Alt+F1, F2, F3, etc)

2. Whenever I go to one of these terminal and then come back to the desktop environment (Ctrl-Alt-F7) i get a big fat red square with the number 1 inside it, as if indicating that it has detected monitor 1. It is the same exact image that appears when identifying monitors throgh AMD's Catalyst Control Center. 

I am unsure if this is the place to report this, but in a sense I would be happy to receive "General Help" to solve the issue.

Regards

---

### Post by lakerssuperman on 2011-05-20
The FGLRX driver has a bug in it that makes the monitors number appear.  Also the resolution of the terminal is different because the proprietary drivers don't support KMS (kernel mode setting) so it doesn't properly detect your monitors resolution.  If you search around and Google a bit I think there is a fix for the monitor number part.

---

### Post by aryzing on 2011-05-20
Thanks for your answer. I forgot to report that I no longer have the problem with the number of the screen appearing. Probably an update fixed it. As for the screen resolution, it is still changed, but I can live with that. 

Thanks againg.

---

