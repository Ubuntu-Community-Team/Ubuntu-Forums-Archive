---
title: "i have messed up my splash screen with plymouth-manager - how to retrieve it ?"
date: 2011-05-14
forum: General Help
---

### Post by doron387 on 2011-05-14
hi
i use ubuntu 10.10
i kind of dislike the ubuntu defauld splash screen (the one with the boring white-orange dots)
i have downloaded plymouth manager 0.74 and insalled it using the softwaare scenter
using this package, i installed few splash screens like sunrise...
my laptop is asus 1201n, screen resolution 1366x768.
after changing the splash screen / plymouth theme i enabled the restricted driver, i had to choose from the resolutions list that was supplied, my resolution did not appear there, so i chose 800x600 8 bit.
when i rebooted the splash was grained and looked awfull.
i uninstalled plymouth manager and now when my system boots i get a black screen with vertical blue lines.
[B]is there a way to go back to 
the boring white-orange dots splash ?[/B]
sometimes it is so exausting to try make things better.....

---

### Post by Dimarchi on 2011-05-14
Try the following:

Open Synaptic, write plymouth in Search and hit enter. Of the packages presented look for plymouth-theme-ubuntu-logo and plymouth-theme-ubuntu-text. If those are not installed, install them. If they are, right click and select Mark for reinstallation.

Other plymouth related packages that you should have installed (note that I have Kubuntu in addition to Ubuntu, so these may vary): libplymouth2, plymouth, plymouth-label.

I think I'm correct in expecting that after installing the themes and rebooting, you will have the default theme back...but at the resolution of 800 x 600 and in 8 bit colour.

---

### Post by doron387 on 2011-05-14
i did it.
now the lines are green and closer one to each other.

---

### Post by doron387 on 2011-05-14
bump...
all i have is white vertical lines on a black background.
please save me guys....
all i ask is go back to the old good (boring) splash screen

is it something with grub-fix or update-grub or something similar ?

i am not an ubuntu expert, so i better not try something that i could not fix later.
waiting for your response

---

### Post by Dimarchi on 2011-05-16
Well, my next step would be reinstallation of all **installed** packages featuring plymouth (follow the steps I mentioned in my previous reply...now right click all packages that are marked installed, select Mark for reinstallation and then Apply). That should force an update. Well, I'm no Ubuntu expert, either. I have found that the steps I have outlined have worked in my case if I have had similar trouble to yours.

---

