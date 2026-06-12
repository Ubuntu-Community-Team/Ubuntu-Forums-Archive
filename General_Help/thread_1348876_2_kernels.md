---
title: "2 kernels"
date: 2009-12-07
forum: General Help
---

### Post by fjm03 on 2009-12-07
Recently gave up on VMware Server 2 under U9.10 (very unstable). Now dual booting U9.10 and W7. Loaded U9.10 last to utilize grub.

Grub showing both the -16 generic and the -17 generic Linux kernels as boot choices.

Can I safely remove the -16 generic folder from root or edit the grub .conf file to remove this apparent nuisance.

If so, how?

---

### Post by coffeecat on 2009-12-07
Two points.

It is not a "nuisance" to have the previous kernel available. If you have problems with the newer kernel, you can boot up into the older one. It is good practice to keep two kernels installed. However, if you do want to uninstall the older kernel, do so with the package manager. Simply deleting the -16 folder and/or editing grub leaves bits and pieces everywhere. It's untidy and the package manager thinks that it's all still installed.

Second point. -17 kernel? Where did that come from? Do you, by chance, have the proposed repository enabled? Is that where it came from? If you do, and it did, you would be exceedingly unwise to uninstall the -16 kernel.

[https://help.ubuntu.com/community/UbuntuUpdates](https://help.ubuntu.com/community/UbuntuUpdates)

>  Enabling the proposed updates repository can break your system. It is not recommended for inexperienced users.

---

### Post by 73ckn797 on 2009-12-07
The kernels can be removed in Synaptic. It is wise to leave it alone until you are certain all is well with the new kernel. I always keep the latest and the last just in case something messes up.

When you uninstall from Synaptic the grub2 menu will no longer show that version as an option.

---

### Post by synapsys on 2009-12-07
The best and easiest thing to do would be to install the 'startup manager'

Open up a terminal 

Applications >> Accessories >> Terminal

And type:

```
sudo apt-get install startupmanager
```Then use startup manager to select how many kernels to display on the boot menu. This way you don't have to worry about losing the older kernel (in case you have issues) and it also won't be displayed every single time you boot.

---

### Post by fjm03 on 2009-12-07
thanks to all. will research -17 and get back.

---

### Post by fjm03 on 2009-12-07
My thanks/apologies to all and to 73ckn797; the kernels were -14 and -16: my bad.

---

