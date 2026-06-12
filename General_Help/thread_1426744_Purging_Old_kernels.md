---
title: "Purging Old kernels"
date: 2010-03-10
forum: General Help
---

### Post by Svechin on 2010-03-10
Ok I'm a Linux newbie, Linux 9.10 GRUB 2. Like others I've noticed kernels accumulating in my GRUB screen and want to keep two but get rid of the older ones for tidiness sake and to make better use of the ten seconds I've got to choose between my two main boot options. Advice I've looked at elsewhere suggests either using synaptic package manager or Ubuntu Tweak. Now I can't seem to download Ubuntu Tweak, and when I use Synaptic Package Manager it only allows me the 'mark for installation' option on all Linux images listed there. Any suggestions how I make Linux package manager do what other posters have suggested it should do, and allow me to mark older kernels for 'mark for removal'? All help appreciated, the number of options plus recovery modes accumulating on GRUB menu is becoming a pain.

---

### Post by plucky on 2010-03-10
> **Svechin said:**
> Ok I'm a Linux newbie, Linux 9.10 GRUB 2. Like others I've noticed kernels accumulating in my GRUB screen and want to keep two but get rid of the older ones for tidiness sake and to make better use of the ten seconds I've got to choose between my two main boot options. Advice I've looked at elsewhere suggests either using synaptic package manager or Ubuntu Tweak. Now I can't seem to download Ubuntu Tweak, and when I use Synaptic Package Manager it only allows me the 'mark for installation' option on all Linux images listed there. Any suggestions how I make Linux package manager do what other posters have suggested it should do, and allow me to mark older kernels for 'mark for removal'? All help appreciated, the number of options plus recovery modes accumulating on GRUB menu is becoming a pain.

Only linux images marked with a green box are the ones that have been installed.All the others have not been installed is the reason that you only have the option to install them.

Post the output from a terminal of ```
ls -l /boot/vmlinuz*
```

Good Luck

---

### Post by drs305 on 2010-03-10
Ubuntu-tweak can be obtained from [http://www.ubuntu-tweak.com]("http://www.ubuntu-tweak.com")

I also have a section on removing older kernels here: 
[ HOWTO: StartUp Manager & Kernel Display Options  ]("http://ubuntuforums.org/showthread.php?t=818177")

---

### Post by hhh on 2010-03-10
Hope this helps...
[http://ubuntuforums.org/showthread.php?p=8923070#post8923070](http://ubuntuforums.org/showthread.php?p=8923070#post8923070)

---

### Post by Svechin on 2010-03-10
Ok, thanks for the replies guys, I'm getting there quickly now.

---

### Post by spiky001 on 2010-03-10
it might be an idea to keep at least 1 old set of kernels just incase the latest 1 lets yo down you will at least be able to get back into the system, i.e keep the newest & the 1 before

---

### Post by Svechin on 2010-03-11
Thanks for all the help guys, the key was synaptic package manager showing much older kernels which are not even installed, never mind uninstalled, as plucky pointed out. Once I clocked that, I uninstalled one of the newer old kernels, leaving two most recent ones for safety, and I am now happy with the GRUB menu. When I uninstalled this, I marked the unwanted kernel as 'for removal' rather than 'remove completely' to be on the safe side. Everything still seems to work fine after actioning the removal, but (last question, promise) is there any big difference between the two options? Thanks again guys, you've been unbelievably friendly and helpful.

---

### Post by drs305 on 2010-03-11
Keeping with the "teach a man to fish" philosophy, take a look at the options in the man page for "apt-get". The some man pages are better than others, but the apt-get man page is pretty thorough.

```
man apt-get
```

Man pages are also available online at various locations if you prefer to view them in html. You can google for a list of sites.

---

### Post by hhh on 2010-03-11
The difference is "complete removal" removes configuration file too. I've always completely removed the old kernels with no ill effects.

---

### Post by scouser73 on 2010-03-11
Removing Old Kernels

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

