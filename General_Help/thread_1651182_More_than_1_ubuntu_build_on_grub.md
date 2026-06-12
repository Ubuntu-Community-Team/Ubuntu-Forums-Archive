---
title: "More than 1 ubuntu build on grub"
date: 2010-12-22
forum: General Help
---

### Post by Dixi1801 on 2010-12-22
Since updating my ubuntu a little while ago, i have more than one linux build on my grub menu.

Is it possible to delete the old build without affecting the current one i'm using?

Thanks in advanced :)

-Dixi

---

### Post by Nytram on 2010-12-22
It's possible to do what you want and remove old kernels/builds. However it's advisable to keep a backup 2nd kernel in case you have problems with your current one. Yeh I know the Grub menu starts to look a bit messy :)

I'm not in Ubuntu right now, but I think theres a Cleanup Janitor in the Preferences menu somewhere which will remove old kernels (probably the easiest way.)

---

### Post by Don Barzini on 2010-12-22
> **Dixi1801 said:**
> Is it possible to delete the old build without affecting the current one i'm using?

Thanks in advanced :)

-Dixi

[http://jaypeeonline.net/tips-tricks/howto-remove-old-ubuntu-kernels/](http://jaypeeonline.net/tips-tricks/howto-remove-old-ubuntu-kernels/)

---

### Post by Dixi1801 on 2010-12-23
Thanks a lot guys, will fix this when I get in tomorrow :)

Have a nice Xmas (providing you celebrate it :p)

-Dixi

---

### Post by TBABill on 2010-12-23
You can also just remove older kernels via Synaptic and you can easily see version numbers to be sure you are marking the correct one for removal. But I would also concur with a previous user to maintain one extra in case something happens and your current one will not boot. Then each time you add a new kernel just keep the current (which becomes the older one) and remove the oldest.

---

### Post by Dixi1801 on 2010-12-24
Using the synaptic package manager worked for me :)

Thanks everyone, for all of your help :)

-Dixi

---

### Post by Nytram on 2010-12-24
Glad to hear you found a solution, merry xmas :)

---

