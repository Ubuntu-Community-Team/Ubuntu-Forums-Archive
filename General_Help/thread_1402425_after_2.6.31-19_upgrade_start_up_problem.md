---
title: "after 2.6.31-19 upgrade start up problem"
date: 2010-02-09
forum: General Help
---

### Post by Lavix on 2010-02-09
I have Ubuntu 9.10 installed inside Windows XP Pro. Everything worked fine.
I updated to 2.6.31-19 version via Update Manager. Now when starting, I always have to choose between previous Ubuntu versions:

Ubuntu, Linux - 2.6.31.19-generic
Ubuntu, Linux - 2.6.31.19-recovery mode
Ubuntu, Linux - 2.6.31.17-generic
Ubuntu, Linux - 2.6.31.17-recovery mode
Ubuntu, Linux - 2.6.31.14-generic
Ubuntu, Linux - 2.6.31.14-recovery mode

When I choose the last version, Ubuntu, Linux - 2.6.31.19-generic or Ubuntu, Linux - 2.6.31.19-recovery mode, nothing happens, the PC rebooted again and again.
When I choose the previous version Ubuntu, Linux - 2.6.31.17-generic, it is loaded without problems.

So I have 2 questions:

1. How is it possible to find an issue and boot from the last installed version Ubuntu, Linux - 2.6.31.19-generic?
2. Is it possible/advised to clear the list of previously installed versions to avoid to choose it every time and to keep the last installed version only?

Thank you.

---

### Post by john newbuntu on 2010-02-09
To get 19 working properly, use the 17 version of the kernel.  Then go to synaptic, mark  the 19 kernel (linux-headers-2.6.31-19 and linux-image-2.6.31-19-generic) for complete uninstallation and re-install them.
As far as removing the other kernels go, the general recommendation is to keep at least the last working kernel or the kernel that came with Karmic (14) and get rid of the rest using Synaptic.

---

### Post by scouser73 on 2010-02-09
> **Lavix said:**
> I have Ubuntu 9.10 installed inside Windows XP Pro. Everything worked fine.
I updated to 2.6.31-19 version via Update Manager. Now when starting, I always have to choose between previous Ubuntu versions:

Ubuntu, Linux - 2.6.31.19-generic
Ubuntu, Linux - 2.6.31.19-recovery mode
Ubuntu, Linux - 2.6.31.17-generic
Ubuntu, Linux - 2.6.31.17-recovery mode
Ubuntu, Linux - 2.6.31.14-generic
Ubuntu, Linux - 2.6.31.14-recovery mode

When I choose the last version, Ubuntu, Linux - 2.6.31.19-generic or Ubuntu, Linux - 2.6.31.19-recovery mode, nothing happens, the PC rebooted again and again.
When I choose the previous version Ubuntu, Linux - 2.6.31.17-generic, it is loaded without problems.

So I have 2 questions:

1. How is it possible to find an issue and boot from the last installed version Ubuntu, Linux - 2.6.31.19-generic?
2. Is it possible/advised to clear the list of previously installed versions to avoid to choose it every time and to keep the last installed version only?

Thank you.

Every time Ubuntu installs a new Linux kernel, the old one is left behind. This means that if you are regularly updating an Ubuntu system the Grub boot menu becomes longer and longer with kernels you don’t need anymore.

The old kernels are deliberately left installed and on the menu so you can boot a previous kernel if you have trouble with a new one. But if the new one works, you can safely uninstall the old kernel, which will also result in the Grub menu being cleaned up.

Follow these steps to identify and remove any old kernels.

**1** - Go to **Terminal** and paste the following command: **uname -r**
It will print the version of the Linux kernel you are running, this is the one you want to keep. It should look something like this: ***2.6.20-16-generic***

**2** - Go to **Synaptic Package Manager** via the **System > Administration** menus

**3** - Paste this: **linux-image-2** into the search box of **Synaptic Package Manager**

**4** - Once you have located the old kernels, **hightlight** them and **right-click** then select **Mark For Complete Removal** then click **Mark** and then click **Apply**

The results should show every available and installed kernel. A green box on the left indicates that the package is installed. The only linux-image you want installed is the latest one.

[COLOR="Red"]**Be careful of what you remove. Ensure that you don’t remove your current kernel, or anything that is not a linux-image. It is possible to break Ubuntu if you remove the wrong kernel.**[/COLOR]

Your computer and Grub menu should now be free of old kernels.

---

### Post by Lavix on 2010-02-09
:frown::frown::frown: May you are too late, scouser73, I did everything as [john newbuntu]("http://ubuntuforums.org/member.php?u=956991") told. After reboot I got the black GNU GRUB version 1.97 beta screen :

Minimal BASH-like editing is supported. For the first word TAB lists possible command completions. Anywhere else TAB lists possible device/file completions.

Now I'm regretting that I had done. "Don't touch the device and it will work forever".

---

### Post by r_s on 2010-02-09
Well , it seems you have wubi installed and it has a bug with grub2 [http://sourceforge.net/apps/mediawik...lems:Wubi_9.10]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10")

---

### Post by warfacegod on 2010-02-09
Please don't hold john newbuntu responsible, it was generally sound advice and something many of us would have suggested as well.

Codes to try from the prompt:

```
sudo update-grub
```

```
startx
```

---

### Post by Lavix on 2010-02-09
No, I've never held  john newbuntu responsible, it was just to post my reply. OK, i'll try the last solution an d let you know.
P.S. Sorry for the delay, I have to reboot.:D

---

### Post by warfacegod on 2010-02-09
Sorry, didn't catch that Wubi install bit. Please disregard my last post and try this:[https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169/comments/210]("https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169/comments/210")

---

### Post by Lavix on 2010-02-09
Yeah, you're right. The command sudo update-grub gave me:
```

unknown command 'sudo'

```I've found the below solution. Could you guide me if it's correct:
```

sh:grub>set root=(loop0)
sh:grub>linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro
sh:grub>initrd /boot/initrd.img-2.6.31-14-generic
sh:grub>boot

```After succeful booting, tape in the terminal:
```

sudo update-grub2

```Your suggestions? There is the only partition on the hard disk, and Ubuntu wubi is installed on 'C' disk.

---

### Post by warfacegod on 2010-02-09
I take it you are able to boot into the 31-14 kernel?

---

### Post by Lavix on 2010-02-09
I haven't tried it yet, waiting for your approval, please. I still have the GRUB black screen when starting.

---

### Post by warfacegod on 2010-02-09
Go ahead, see if it works. If so, get all updates.

---

### Post by Lavix on 2010-02-09
The steps I described earlier worked for me at 100%. Thanks a lot to everybody for the participation.

---

### Post by john newbuntu on 2010-02-09
Lavix, My sincerely apologies if I misguided you or if you misunderstood me.  That was not deliberate.  My suggestion was only to remove the newer kernel, go back to an older working one and then re-install the new one as I suspected something might have gone wrong in the install of new kernel.  I have done this on my machine some time back and has worked successfully although I do not use WUBI.

Yes, your commands seem to be correct to boot from the command line.
Run it and let us know how it works.
Once again sorry for the trouble.

---

### Post by Lavix on 2010-02-09
@[john newbuntu]("http://ubuntuforums.org/member.php?u=956991"): No worry, as I already told, everything is in order now and works as before.

---

### Post by warfacegod on 2010-02-09
I guess Marking as Solved under Thread Tools would be in order then. I'll keep my subscription to the thread for a few days in case you have another issue with this.

---

