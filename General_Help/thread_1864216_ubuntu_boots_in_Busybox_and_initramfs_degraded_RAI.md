---
title: "ubuntu boots in Busybox and initramfs degraded RAID"
date: 2011-10-18
forum: General Help
---

### Post by alfonso78 on 2011-10-18
do you get something like this when booting Ubuntu?

(I copied this from an other post, version numbers are probably wrong)

```
Busybox v1.15.3 (Ubuntu 1:1.15.3-1ubuntu5) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)
```

chances are, you have a RAID array which needs recovery

I'm assuming that typing "exit" at the prompt allows you to boot your system (this was my case)

So first you want to know what's going on, so edit /etc/default/grub and comment (put # at the beginning) the line:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

don't forget to apply changes:

```
sudo update-grub
```

Then reboot your box and you will see what is the problem. In my case Grub was kind enough to ask me:

```
Do you wish to start the degraded RAID?
```

except the question was hidden by the splash screen (nice, uh?)

So now you google some more and bump into this:
[https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/268873](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/268873)

so you edit again /etc/default/grub so that you bring back the splash screen and tell grub to boot anyway:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
#GRUB_CMDLINE_LINUX=""
GRUB_CMDLINE_LINUX="bootdegraded=true"
```

don't forget to apply changes:

```
sudo update-grub
```

Next reboot should not hang anymore!

hope this helps!

---

