---
title: "Quick question about upgrade themes"
date: 2009-08-09
forum: General Help
---

### Post by waraas on 2009-08-09
Hello,

I had recently upgraded my main computer to the newest release, and I just installed the latest release onto my laptop. However the 2 themes are different, the theme on my main computer has been the same one ever since I first installed it like 2-3 years ago. 

I like the new theme that is on my laptop. The splash page is better looking (glossy) and it looks like some of the icons are upgraded a little. Can someone tell me how to upgrade to get it for my main computer?

My main system says I have no updates available. I type is lsb_release -a and got the info below:

Main computer:
Distributor ID:    Ubuntu
Description:    Ubuntu 8.04.3 LTS
Release:    8.04
Codename:    hardy


Laptop:
Distributor ID:    Ubuntu
Description:    Ubuntu 9.04
Release:    9.04
Codename: juanty

How do I upgrade to get the 9.04 release? Thanks in advance :)

---

### Post by howefield on 2009-08-09
You will need to upgrade to Jaunty in two stages, ie, first to Intrepid then to Jaunty. If you want to do this, comment out all ppa's you have enabled, update Hardy,  then press Alt-F2 and type:

```
gksu update-manager -d
```

This will give you Intrepid, then repeat to get to Jaunty.

If it were mine, I'd download Jaunty and burn to a cd and try out in in Live mode to make sure everything worked well and then do a clean install.

---

