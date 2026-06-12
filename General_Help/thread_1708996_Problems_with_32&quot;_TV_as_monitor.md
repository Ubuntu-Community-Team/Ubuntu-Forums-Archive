---
title: "Problems with 32&quot; TV as monitor"
date: 2011-03-17
forum: General Help
---

### Post by kevinvugs on 2011-03-17
My system is setup as follows...

Custom Build 
EVGA 730a motherboard with onboard GeForce 8200 512mb
3 gb 6400 ram 
AMD atholon dual core 2.7ghz overclocked to 3.5 ghz 

Brand new Vizio 32" hooked through HDMI cable

Ubuntu 10.10 (maverick)
Nvidia drivers installed and working (able to use compiz without issue)

Although it is more of an annoyance then a problem, when I am scrolling up or down either in Firefox or in a directory like pictures, I get a "double" image. I have included a screenshot to show what I am talking about.

---

### Post by LowSky on 2011-03-17
Follow these commands to install the newest version of the nvidia driver (10.10 is a bit behind)

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates

sudo apt-get update && sudo apt-get upgrade

sudo apt-get install nvidia-current nvidia-current-modaliases nvidia-settings
```

it can also be a compiz issue... tyr turning it off afterwards if the issue continues... we can then tryin fixing that if needed.

---

