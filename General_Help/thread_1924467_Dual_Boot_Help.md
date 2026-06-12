---
title: "Dual Boot Help"
date: 2012-02-12
forum: General Help
---

### Post by bOgNeR17 on 2012-02-12
First I installed Lubuntu, and then I decided that I would install Ubuntu alongside it so I could get the best of both of them. In the setup of Ubuntu I selected for it to be install along side of the current "Ubuntu" and I partitioned the drives and split them in two. When I boot up my I system I do not know what to select for lubuntu to boot up. Anyone know what to do?

---

### Post by Rex Bouwense on 2012-02-12
Welcome to the forums.  When you boot a screen will appear that has a list.  On that list will be Lubuntu, a Lubuntu recovery mode, Ubuntu, a Ubuntu recovery mode, and a memory test.  If you installed Ubuntu second it will probably be on the top and will be the default OS.  To choose Lubuntu just use the down arrow on the key board to highlight Lubuntu and press enter.  That should be all that you need.  If you want to change the boot order, I would use Grub Customizer.  See:

[http://www.ubuntugeek.com/grub-customizer-2-2-released-and-installation-instructions-included.html](http://www.ubuntugeek.com/grub-customizer-2-2-released-and-installation-instructions-included.html)

---

### Post by JC Cheloven on 2012-02-12
Side note: for a future occasion, you may consider more efficient installing only one operating system, and then installing inside it an extra desktop environment. For example, installing regular ubuntu, then the lubuntu-desktop package. You could choose what DE you want to use for each session at the time of login.

---

### Post by drs305 on 2012-02-12
In addition to changing the boot order, Grub Customizer can tweak the titles so you can make the selections a bit easier to recognize. I have a link to Grub Customizer in my signature line.

Meanwhile, decide which installation you want to be primary, boot into it, and run:
```
sudo grub-install /dev/sda
```

That will make that OS's Grub the default, and place that OS first in the menu.

---

### Post by bOgNeR17 on 2012-02-12
Thank you, the problem that threw me off and confused me is that it recognized Lubuntu as Ubuntu and named it "Ubuntu" instead on the list so I had two Ubuntu options from the boot menu so I just clicked on the second one and Lubuntu booted up fine. Is there anyway that I could rename it to Lubuntu just for handiness? Again thanks for the quick reply. :KS

> In addition to changing the boot order, Grub Customizer can tweak the  titles so you can make the selections a bit easier to recognize. I have a  link to Grub Customizer in my signature line.

Thanks drs305 you answered my question cheers.

---

