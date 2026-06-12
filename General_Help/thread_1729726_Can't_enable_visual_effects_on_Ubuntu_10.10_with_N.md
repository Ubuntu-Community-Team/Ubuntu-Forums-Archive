---
title: "Can't enable visual effects on Ubuntu 10.10 with Nvidia GT 425m"
date: 2011-04-15
forum: General Help
---

### Post by MiloshMobile on 2011-04-15
First off I am EXTREMELY new to Linux but I am familiar with the console and basic commands. I installed ubuntu on my Sony VPCF13YFX laptop and have had graphical nightmares. First, when I installed the Nvidia driver automatically through the "restricted drivers" option my computer would hang at a purple screen on reboot. I managed to install the newest drivers manually and it seems to work now. The only thing i can't figure out is that when i go to enable visual effects (either normal or extra) it says "looking for drivers" and then "cannot enable visual effects". I have looked around and found a few posts on ATI and Intel chipsets but nothing for Nvidia. Any help would be greatly appreciated.

---

### Post by 3Miro on 2011-04-15
Nvidia GT 425m uses Optimus technology. Nvidia has decided that they will provide neither Linux drivers nor needed specifications so the community can make such drivers. There is a petition form the community to change that, but any change will take some time. At this point, there is little hope of getting things to wok better.

Note that older Nvidia cards and Nvidia on desktop is the best thing for Linux. ATI 4xxx and newer also work great. Intel has long tradition of providing good drivers (except for the latest Netbook video cards that had drivers, but very buggy ones). It is just that for your specific video card, the Nvidia corporation has decided that they don't want you to use Linux.

After some Googling, it seems that you can turn off one of the two hybrid graphics cards from the BIOS (or at leas on some BIOS). If you do that, then things will hopefully work reasonably well (I don't think you will be able to get visual effects though).

---

### Post by MiloshMobile on 2011-04-15
Thanks for your prompt response. The graphics seem to perform pretty well but that sucks i won't be able to use visual effects. Oh well, i guess i'll just wait on Nvidia to do something about this.

---

### Post by 3Miro on 2011-04-15
> **MiloshMobile said:**
> Thanks for your prompt response. The graphics seem to perform pretty well but that sucks i won't be able to use visual effects. Oh well, i guess i'll just wait on Nvidia to do something about this.

You can try making more searches for Optimus to see what work-arounds people are using, but from what I could find only disabling one video card from the BIOS can help.

---

### Post by MiloshMobile on 2011-04-15
People have said that the only way to get it to work is to disable the card in bios but i dont have that option. Also, i was unaware that my laptop even had multiple graphics adapters.

---

