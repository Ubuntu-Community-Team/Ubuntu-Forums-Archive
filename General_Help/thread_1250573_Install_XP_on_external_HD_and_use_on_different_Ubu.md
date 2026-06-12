---
title: "Install XP on external HD and use on different Ubuntu boxes"
date: 2009-08-26
forum: General Help
---

### Post by nbo10 on 2009-08-26
I love using ubuntu but there are a few programs from hardware companies that only run on windows. Could I install XP on an external HD and then just boot to the external HD when I need t use XP? Or should I still use grub? Any risk to my internal harddrives while installing XP to an external HD? Thanks

---

### Post by PeEllAvaj on 2009-08-26
Windows tends to bind itself to any hardware configuration (as well as serial numbers) at install, so you won't be able to use the same external HDD on different boxes, but you should be able to use a single HDD on a single box.

Windows XP can definitely overwrite your Master Boot Record, and make it impossible to boot up grub or Ubuntu.  If you wanted to be 100% safe during the installation, I would unplug your internal drives during the windows installation, and then plug everything back in and update Grub under Ubuntu, it should find your windows XP and allow you to boot to it at will.

I would also like to recommend you try a virtual machine, such as VirtualBox for your windows installation to prevent it from ruining your main Ubuntu machine.

---

### Post by nbo10 on 2009-08-26
It's going to be on a laptop. So I can't unplug the internal harddrive. Grub will automaticly find the windows installed on the external HD? Thanks

---

### Post by mike555 on 2009-08-26
I think Grub will freak if the external hard drive is not always plugged in ...... you might use a different boot manager like " GAG " ...........  [http://gag.sourceforge.net/](http://gag.sourceforge.net/)   .. it's very easy to set up and works great for me on my experimental computer in the back room .......... it boots up to 9 different OS's (just install Ubuntu's or whatever's grub to the same partition you install on .... it works with multi-installs of XP also ........

---

