---
title: "System boot screwed, /lib/modules missing"
date: 2011-09-03
forum: General Help
---

### Post by requeth on 2011-09-03
Howdy,

I'm running Ubuntu 10.10 64 bit, fairly standard install. It's been working for about a year now.

So, I did a 'sudo shutdown now' on my system, and when I started it back up and tried booting my latest and 2nd latest kernel I was thrown into an initramfs shell.

I was able to boot into the original kernel that I installed Ubuntu with, I believe it was 2.6.X.23. I havn't upgraded in a while so my latest was a .26.

So, I log in and everything seems to be running fine. I did an apt-get update and then a system wide upgrade and apt re-installed every single application on my system, even if the version hadn't changed.

At the end of those upgrades it tried reinstalling all of the kernels but failed stating /lib/modules is missing. I verified this is in fact missing, which is strange because I know it was there before this all started.

At first I was thinking my HD died, but my windows 7 partition runs fine.

I have no idea how to fix this, and I'm afraid to reboot now that /lib/modules is missing. I've tried updating the kernels and reconfiguring the kernels, but I'm given errors stating the kernel isn't found, yet when I run an apt-get upgrade it sees the kernel but still tries to re-install it (along with everything else).

Any ideas? If I reboot will the system eat itself?

---

### Post by dino99 on 2011-09-03
boot in recovery mode & select "repair packages", then update grub:

sudo grub-mkconfig
sudo update-grub

---

