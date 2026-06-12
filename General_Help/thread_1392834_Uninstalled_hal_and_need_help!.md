---
title: "Uninstalled hal and need help!"
date: 2010-01-28
forum: General Help
---

### Post by askinne2 on 2010-01-28
Hey guys. I uninstalled hal with plans to reinstall. But the system rebooted before a reinstall. Now Im stuck in the terminal environment only. How do you reinstall hal? Obviously I cannot use Synaptic because I cant get to the desktop. Im pretty new to this stuff so noob it up for me. Thanks guys!

ps - is the internet not going to work since hal is uninstalled? Will plugging it in directly via ethernet cord work?

---

### Post by DoubleDown on 2010-01-28
> **askinne2 said:**
> Hey guys. I uninstalled hal with plans to reinstall. But the system rebooted before a reinstall. Now Im stuck in the terminal environment only. How do you reinstall hal? Obviously I cannot use Synaptic because I cant get to the desktop. Im pretty new to this stuff so noob it up for me. Thanks guys!
 
ps - is the internet not going to work since hal is uninstalled? Will plugging it in directly via ethernet cord work?
 
I removed hal in windows once (it was called hall.dll) and I could never get it to work again, so there's a good bet your Ubuntu installation won't work anymore either. Plugging it in directly via ethernet cord won't work - it needs hal in order to operate (hardware abstraction layer).  I think what you need is a nice, fresh, clean install.

---

### Post by askinne2 on 2010-01-28
I would love to do that but the reason that I was messing with hal in the first place was to get my cd drive working again. Is there another option on installing ubuntu?

---

### Post by falconindy on 2010-01-28
> **DoubleDown said:**
> I removed hal in windows once (it was called hall.dll) and I could never get it to work again, so there's a good bet your Ubuntu installation won't work anymore either. Plugging it in directly via ethernet cord won't work - it needs hal in order to operate (hardware abstraction layer).  I think what you need is a nice, fresh, clean install.

HAL in Windows isn't the same as HAL in Linux. From the terminal just type 'sudo apt-get install hal' (or at least i think that's the package name).

---

### Post by DoubleDown on 2010-01-28
> **askinne2 said:**
> I would love to do that but the reason that I was messing with hal in the first place was to get my cd drive working again. Is there another option on installing ubuntu?
 
As far as I know, hal is one of those files you just don't mess around with.  It's like deleting the whole operating system.  The only other solution I could suggest is to contact Canonical and ask for a supervisor.  If you explain the situation to them they may send you a replacement cd.

---

### Post by DoubleDown on 2010-01-28
> **falconindy said:**
> HAL in Windows isn't the same as HAL in Linux. From the terminal just type 'sudo apt-get install hal' (or at least i think that's the package name).
 
Wow I've never heard of any such thing! Sorry - guess I was mistaken.

---

### Post by askinne2 on 2010-01-28
Thanks for the reply! I used the command it it says that hal is installed. But on reboot Im still stuck in the terminal environment for some reason.

Any ideas? Any command I can run and give you the output that might help?? I would have to manually copy everything that output gives me though.

---

### Post by undecim on 2010-01-28
you probably uninstalled GDM at the same time you uninstalled HAL. Just "sudo apt-get install gdm" should fix that.

EDIT: There are also some gnome packages that depended on HAL or GDM. If you find that you are still having problems after reinstalling GDM, "sudo aptitude install ubuntu-desktop" will install every package that comes in the default install.

---

### Post by askinne2 on 2010-01-28
Well that almost did the trick! It got me all the way through logging in normally. Now its basically my desktop with a white square that is the terminal and nothing else. So obviously that helped alot. I tried to use the ubuntu-desktop command. It said that 62 would be newly installed but once I choose yes to install it gave me errors listing a bunch of websites. Any ideas?

---

### Post by askinne2 on 2010-01-28
Ok, I missed the aptitude instead of apt-get. It worked! Thanks so much!

---

