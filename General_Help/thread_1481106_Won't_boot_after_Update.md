---
title: "Won't boot after Update"
date: 2010-05-12
forum: General Help
---

### Post by m3k on 2010-05-12
I installed Kubuntu Lucid 10 days ago and it all went pretty smooth aside from the Plymouth res issue which I fixed following some online tutorial. It was working fine until yesterday when I updated the system. I think the update was primarily nvidia and maybe a new kernel, among other packages.

Now it won't boot... Plymouth shows then it goes to a blank screen, it looks like it's still working cause Ctrl + Alt + Del makes it reboot, but I can't get Ctrl + Alt + F1 to do anything and I can't get it to boot in Text mode (not sure if this was changed in Lucid). Also I can't access GRUB, it simply doesn't show up after holding Shift or any other key.

So I'm left with a completely unusable system and not sure how I can debug it since I can't get a console? Any hard way to make it boot into text mode?

---

### Post by m3k on 2010-05-12
It seems the problem was the nvidia update didn't went very good. This is how I fixed it:

I fired up the Live CD and chrooted into my Linux install, you can find instructions on how to do it here:

[http://superuser.com/questions/111152/whats-the-proper-way-to-prepare-chroot-to-recover-a-broken-linux-installation](http://superuser.com/questions/111152/whats-the-proper-way-to-prepare-chroot-to-recover-a-broken-linux-installation)

I attempted to reinstall nvidia-current and it said something about missing source for the current kernel so it wasn't building it. So I installed the linux-headers for my kernel and then reinstalled nvidia-current. That's it.

---

