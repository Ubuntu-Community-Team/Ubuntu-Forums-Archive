---
title: "GRUB help - so many kernels listed!"
date: 2010-01-18
forum: General Help
---

### Post by Pauly BC on 2010-01-18
How can I shorten the list of kernels offered by the boot menu? It currently offers four options, each with a safe mode. The list is too long. Is there a way to limit it to the current version and one previous version?

---

### Post by akakingess on 2010-01-18
Just install Startup Manager (available in the Ubuntu Software Center and Synaptic Package Manager) and it will give you the option of how many kernels to show within the GRUB menu.

---

### Post by audiomick on 2010-01-18
It is not a bad idea to keep at least two, so you can still boot into the older one if the current one gets messed up.

---

### Post by wilee-nilee on 2010-01-18
If your version of startup manager does not limit the kernels showing, you can remove them from synaptic, but only if you know what your doing.

I use ubuntu tweak for a lot of things it will actually remove the kernels you want from the computer and grub here is the ppa link.
[https://launchpad.net/~tualatrix/+archive/ppa](https://launchpad.net/~tualatrix/+archive/ppa)

If your familiar with how to pull the link to the sources list and the key this should be helpful.

---

### Post by Cheesemill on 2010-01-18
Or you can fire up Synaptic and uninstall any old kernels, this will update the boot menu as well.

As audiomick says, it's always best to keep the current kernel (obviously) and one previous kernel.

---

### Post by 7raTEYdCql on 2010-01-18
You can manuall comment the lines in /boot/grub/grub,cfg.

I would seriously not advise that, and prefer you using startup manager for it.

---

### Post by TetonsGulf on 2010-01-18
FROM: [http://tuxtweaks.com/2009/12/remove-old-kernels-in-ubuntu/](http://tuxtweaks.com/2009/12/remove-old-kernels-in-ubuntu/)

Don't follow this process unless you're sure you don't need to boot into the older kernels. If you're not sure, just leave things alone. Also, it is possible to remove all of the kernels from your system and make it unbootable. I suggest leaving the latest kernel and one version previous to that. You can find out the kernel version that you're currently running with

```
uname -r
```

**Find and remove old kernels**

The first step is to figure out what kernels are installed. The following command will do the job.

```
ls /boot | grep vmlinuz | cut -d'-' -f2,3
```

Your result should look something like this.
```
2.6.28-15
2.6.28-16
2.6.28-17
```

This is the list of kernels installed on your system. Now you want to find out which packages are installed relative to the kernel you want to remove. For my example I'm going to remove the oldest one, 2.6.28-15.

```
dpkg -l | grep ^ii | grep 2.6.28-15 | awk -F' ' '{ print $2 }'
```

On my system, (Jaunty) the resulting list is:
```
linux-headers-2.6.28-15
linux-headers-2.6.28-15-generic
linux-image-2.6.28-15-generic
linux-restricted-modules-2.6.28-15-generic
```

Now that we know what packages to remove we can remove them with dpkg, apt-get or aptitude.

```
sudo aptitude remove linux-headers-2.6.28-15 linux-headers-2.6.28-15-generic linux-image-2.6.28-15-generic linux-restricted-modules-2.6.28-15-generic
```

That's it. You've removed an old kernel and related packages.

---

### Post by r_s on 2010-01-18
Remove old kernels using synaptic package manager and then update your grub file
sudo update-grub.

---

