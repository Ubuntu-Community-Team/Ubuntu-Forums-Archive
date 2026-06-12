---
title: "Don't Want To Upgrade Kernel"
date: 2006-03-23
forum: General Help
---

### Post by reidbold on 2006-03-23
Hi folks, i've got a problem here. In order to run the nvidia module I had to compile my own kernel. I couldn't get it working using either of methods 1 or 2 from this guide [http://www.ubuntuforums.org/showthread.php?t=75074]("http://www.ubuntuforums.org/showthread.php?t=75074"). 

So I built a 2.6.12 kernel myself and everything is swell. Except now everytime I want to upgrade using synaptic, it insists on installing it's own kernel and headers. In particular
linux-headers-2.6.12-10
linux-headers-2.6.12-10-386
linux-headers-386
linux-image-2.6.12-10-386

I'm not really interested in installing these since they'll probably break my nvidia driver. So is there a way to ignore upgrading these components?

---

### Post by Zeroangel on 2006-03-23
Have you tried uninstalling linux-386 ? Uninstalling that metapackage should also uninstall the kernel update features.

Although, if i'm not mistaken, Breezy is now using 2.6.13-x kernels so it might be a good idea to compile one of those in the meantime.

---

### Post by Matt Yun on 2006-03-24
apt-get doesn't replace your kernel; your old one is still around in /boot, and the sources still in /usr/src.  Just edit /boot/grub/menu.lst, go to the end of the file, and comment out the new kernel entries.

---

### Post by japs_it88 on 2006-03-24
[QUOTE=Zeroangel]Have you tried uninstalling linux-386 ? Uninstalling that metapackage should also uninstall the kernel update features.

Although, if i'm not mistaken, Breezy is now using 2.6.13-x kernels so it might be a good idea to compile one of those in the meantime.[/QUOTE]


I'm using Breezy and always take my system up to date, and I have kernel 2.6.12-10-386

---

### Post by trent dillman on 2006-03-24
I upgraded my kernel after compiling my own kernel (for swsusp) and my nvidia driver from 2.6.12-10 to whatever the newest one was, and it was fine. I think it was a patch though. You could try upgrading, and as Matt said, your old kernel will still be there just in case...

---

### Post by Zeroangel on 2006-03-24
Ah, my mistake then. I thought Breezy was using the 2.6.13 kernels.

---

### Post by dcstar on 2006-03-24
[QUOTE=reidbold]Hi folks, i've got a problem here. In order to run the nvidia module I had to compile my own kernel. I couldn't get it working using either of methods 1 or 2 from this guide [http://www.ubuntuforums.org/showthread.php?t=75074]("http://www.ubuntuforums.org/showthread.php?t=75074"). 

So I built a 2.6.12 kernel myself and everything is swell. Except now everytime I want to upgrade using synaptic, it insists on installing it's own kernel and headers. In particular
linux-headers-2.6.12-10
linux-headers-2.6.12-10-386
linux-headers-386
linux-image-2.6.12-10-386

I'm not really interested in installing these since they'll probably break my nvidia driver. So is there a way to ignore upgrading these components?[/QUOTE]
If you don't want to get upgrade prompts for any package, go into Synaptic, select the packages and set the "Locked Version" option.

---

### Post by reidbold on 2006-03-25
dcstar, perfect! Thanks.

---

