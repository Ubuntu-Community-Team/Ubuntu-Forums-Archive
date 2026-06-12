---
title: "Different Kernels choice during Boot..What for?"
date: 2009-09-23
forum: General Help
---

### Post by Saurabhdua on 2009-09-23
Hello There!:)

I have dual OS loaded PC. I have observed that UBUNTU lists in total of 4 choices at the Boot Screen.

Ubuntu Kernel *.*.*.15 & 11 & their corresponding "Recovery Modes"...What for? Where exactly does this make a difference?

Please be a bit elaborative against its explanation..! :guitar:

---

### Post by nothingspecial on 2009-09-23
Sometimes, when you update your system to a new kernel, some part of your system can break (sound, wireless etc). You can then boot into the previous working kernel so you can listen to music and surf while you investigate the problem.

It`s a good idea to keep them around, just incase.

---

### Post by scouser73 on 2009-09-23
Every time Ubuntu installs a new Linux kernel, the old one is left behind. This means that if you are regularly updating an Ubuntu system the Grub boot menu becomes longer and longer with kernels you don&#8217;t need anymore.

The old kernels are deliberately left installed and on the menu so you can boot a previous kernel if you have trouble with a new one. But if the new one works, you can safely uninstall the old kernel, which will also result in the Grub menu being cleaned up.

Follow these steps to identify and remove any old kernels.

**1** - Go to **Terminal** and paste the following command: **uname -r**
It will print the version of the Linux kernel you are running, this is the one you want to keep. It should look something like this: ***2.6.20-16-generic***

**2** - Go to **Synaptic Package Manager** via the **System > Administration** menus

**3** - Paste this: **linux-image-2** into the search box of **Synaptic Package Manager**

**4** - Once you have located the old kernels, **hightlight** them and **right-click** then select **Mark For Complete Removal** then click **Mark** and then click **Apply**

The results should show every available and installed kernel. A green box on the left indicates that the package is installed. The only linux-image you want installed is the latest one.

[COLOR="Red"]**Be careful of what you remove. Ensure that you don&#8217;t remove your current kernel, or anything that is not a linux-image. It is possible to break Ubuntu if you remove the wrong kernel.**[/COLOR]

Your computer and Grub menu should now be free of old kernels.

---

### Post by DFlame on 2009-09-23
Nothing to worry about here :)

What you are seeing is the same installation of Ubuntu, but with the option to boot two different kernels. x.15 is obviously the later version, and it was added to the menu when you updated your Ubuntu installation.

x.11 remains there merely as a failsafe. If for some reason the x.15 kernel caused trouble, you could boot into your older kernel instead of being locked out of your system.

As for what to do with it, it is wise to leave it there. It does no harm but can do a lot of good should you ever need to fall back ;)

---

### Post by Saurabhdua on 2009-09-24
Thanks! What a Cheeky, Short & Crisp reply!...Great!

I believe it is equivalent to Windows option that says::"Last Known Good Configuration"...Isn't it?

---

### Post by Saurabhdua on 2009-09-24
Thanks Scouser73!

That was the one I was looking for!...Great! You taught me the whole procedure like a Veteran does for his subject!

Kudos & Hats off to ur expertise!

---

### Post by Saurabhdua on 2009-09-24
Ok that's Great!

But...Will it help me save some "Disk Space" if I decide to get rid of the Previous kernel? If so...how much?

---

### Post by ibuclaw on 2009-09-24
> **Saurabhdua said:**
> Thanks! What a Cheeky, Short & Crisp reply!...Great!

I believe it is equivalent to Windows option that says::"Last Known Good Configuration"...Isn't it?

Actually, last known good configuration works slightly different.

LKGC is login orientated (ie: whenever you login, a LKGC is created). inside it is are the configuration and drivers used to log you in successfully.
If you can't login under new configuration, then LKGC will boot windows using the configuration that allowed you to login last.

Multiple kernels are just that, multiple kernels.

Something similar to a last good configuration would be to backup your initrd.img file and create a boot stanza to boot Linux using it before running the 'update-initrd' command. But ramdisks only cover the drivers/files needed to boot Linux, so a "last good boot" would be a better name to call it.

Regards
iain

---

### Post by ibuclaw on 2009-09-24
> **Saurabhdua said:**
> Ok that's Great!

But...Will it help me save some "Disk Space" if I decide to get rid of the Previous kernel? If so...how much?

About 100MB per kernel in Ubuntu, size varies over time ... and I guess it will only get bigger the more drivers Linux supports.

---

