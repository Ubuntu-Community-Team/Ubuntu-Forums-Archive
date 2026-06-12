---
title: "Removing the nouveau driver"
date: 2010-06-16
forum: General Help
---

### Post by rasmus91 on 2010-06-16
Hi

I did something stupid: I installed the nVidia 3rd party driver before removing the Nouveau Driver, this means that when my computer is done booting i'll just have a black screen, being able to do nothing.

Can i somehow solve this using a live CD? or is there a simpler way?

Ubuntu can't boot in recovery mode neither, so it kinda sucks. Anyway, i'd like someone to tell me how to do this.

Thanks.

And one more thing, does anyone know from where i can download a linux Atheros wireless driver?

---

### Post by warfacegod on 2010-06-16
"startx" work?

---

### Post by rasmus91 on 2010-06-16
Sorry man, can't go to terminal or anything -.-

---

### Post by warfacegod on 2010-06-16
Might be easiest and safest to simply reinstall Ubuntu.

---

### Post by rasmus91 on 2010-06-16
... Again?! *sigh*

---

### Post by warfacegod on 2010-06-16
You could always wait and see if anybody else has a better solution. If reinstalling such a chore perhaps you should create a Home partition and mark it as such during your next install and move all of your files. Your settings will be stored there and if you ever reinstall/upgrade they'll still be in place and active.

---

### Post by philinux on 2010-06-16
> **rasmus91 said:**
> Hi

I did something stupid: I installed the nVidia 3rd party driver before removing the Nouveau Driver, this means that when my computer is done booting i'll just have a black screen, being able to do nothing.

Can i somehow solve this using a live CD? or is there a simpler way?

Ubuntu can't boot in recovery mode neither, so it kinda sucks. Anyway, i'd like someone to tell me how to do this.

Thanks.

[http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)

Use this as a guide to get into a chroot. Don't reinstall grub but use the chroot to remove the nvidia driver. You didn't need to remove nouveau anyway the nvidia installer takes care of it all. Well, should do.

Once you in the livecd chroot. Do this.

```
sudo apt-get remove nvidia-current
```

Then reboot and see if you're back up and running.

If you get stuck use firefox and the livecd and post here.

---

### Post by rasmus91 on 2010-06-16
> Then reboot and see if you're back up and running.

Hmm, just figured out by my self how chroot works, removed the nouveau :( But i will do as you suggest and try removing the nvidia driver :( it just sucks, Any ideas as how to get the nvidia driver working?

(btw im dualbooting with doh!s 7)

---

### Post by philinux on 2010-06-16
> **rasmus91 said:**
> Hmm, just figured out by my self how chroot works, removed the nouveau :( But i will do as you suggest and try removing the nvidia driver :( it just sucks, Any ideas as how to get the nvidia driver working?

(btw im dualbooting with doh!s 7)

Without nouveau or nvidia-current I'm not sure what you will get. Maybe low res graphics, but hey thats a start.

What card it is you got.

---

### Post by rasmus91 on 2010-06-16
nVidia GeForce 330m GT

btw: acer aspire 5745G

just reinstalled ubuntu

---

