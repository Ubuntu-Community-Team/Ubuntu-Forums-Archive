---
title: "Ubuntu 9.04, odd startup environment"
date: 2009-10-24
forum: General Help
---

### Post by lu6cifer on 2009-10-24
For the last couple of months, whenever I started up Ubuntu, there'd be this routine disk check. It would always stop at 70% at /dev/sda7 (my /home), and then it would go to a cmd line interface, a bunch of stuff would scroll through, and it would end with a root terminal, telling my to check my filesystem.

It also gave me the option to ignore the filesystem check, and boot up regularly. So, that's what I did. To avoid this annoying disk check, I just didn't restart/turn off ubuntu for a couple of months. 

Just recently, I had to boot into Windows, and upon rebooting into Ubuntu, I encountered a problem: My desktop, shortcuts, files, installed programs, etc... were all gone. In fact, when I bootup into Ubuntu, it's a completely different environment--the default Jaunty environment, with three desktop backgrounds, firefox 3.0, etc...

What's weird is, I think my home folder and root folder are still there. I checked Gparted, and my /dev/sda6 and /dev/sda7 still have the same amount of used disk space. It's just for some reason, Ubuntu decided to start me up in this weird environment. 

Any help?

Edit: Oh, and I did do a fsck on /dev/sda6 with the recovery mode option in GRUB...it didn't fix anything..

---

