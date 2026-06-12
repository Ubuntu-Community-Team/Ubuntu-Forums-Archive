---
title: "Dual Boot computer no longer offers Windows"
date: 2011-03-29
forum: General Help
---

### Post by Gary100 on 2011-03-29
Hi,

I'm using a dual boot computer which originally had only windows XP, and I added Ubuntu to make it a dual boot. I now have Ubuntu 10.04 and windows XP

I installed PHP, MySql and Apache using this guide:

[http://harx.nl/component/content/article/2-linux/32-installphpapachemysqlubuntu1010](http://harx.nl/component/content/article/2-linux/32-installphpapachemysqlubuntu1010)


It seemed to work perfectly.

My problem is that when I shut down and restart, I no longer have the option to choose windows. Must I blank out the disk and reinstall EVERYTHING from the start, or is there any way to save this? My Ubuntu setup is much simpler than my windows, and if I MUST sacrifice one, it has to be Ubuntu, because it will be much easier to duplicate my ubuntu work than my windows work.

Thanks,
Gary

---

### Post by mendhak on 2011-03-29
Hi, have a look at this community page here:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

If you can see the partition on which you have Windows, you can get the information you need out and then add it to your grub.

---

### Post by Grenage on 2011-03-29
> **Gary100 said:**
> Hi,

I'm using a dual boot computer which originally had only windows XP, and I added Ubuntu to make it a dual boot. I now have Ubuntu 10.04 and windows XP

I installed PHP, MySql and Apache using this guide:

[http://harx.nl/component/content/article/2-linux/32-installphpapachemysqlubuntu1010](http://harx.nl/component/content/article/2-linux/32-installphpapachemysqlubuntu1010)


It seemed to work perfectly.

My problem is that when I shut down and restart, I no longer have the option to choose windows. Must I blank out the disk and reinstall EVERYTHING from the start, or is there any way to save this? My Ubuntu setup is much simpler than my windows, and if I MUST sacrifice one, it has to be Ubuntu, because it will be much easier to duplicate my ubuntu work than my windows work.

Thanks,
Gary

From a terminal, type:

```
sudo update-grub
```

See if that helps.

---

### Post by Rubi1200 on 2011-03-29
And if Grenage's suggestion does not work, post the results of the boot info script.

There is a link at the bottom of my post with instructions.

---

### Post by Gary100 on 2011-03-29
The solution I found was so simple, I'm embarrassed to admit it, but since it might help someone else:

I was absent from Ubuntu for a while, and Update Manager installed quite a bit of code. It gave me a few extra "boot" options, pushing Windows XP down the list - off the first page! All I had to do was scroll down, and there was Windows XP, as plain as could be!

---

### Post by Hedgehog1 on 2011-03-29
Yeah!!!! Easiest fix this week!!!!

***The Hedge***

:KS

*(Now I am just waiting from him to ask how to get rid of the older kernals from the grub menu list)* :D

---

### Post by oldfred on 2011-03-30
That little tiny arrow on the right side of the grub menu/box is the only thing that says more or scroll down. First time for me I also was lost.

@The Hedge
Well you said he would ask why not just post the answer:

Check current kernel, Make sure you do not delete current kernal & it is best to keep one extra older one just in case:
lsb_release -a
Go to Synaptic Package Manager and search for linux-image.
More info in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)

I have not used the newer GUI tools.
HOWTO: Grub Customizer 
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)
HOWTO: Remove Older Kernels via GUI Tweak
[http://ubuntuforums.org/showthread.php?t=1587462](http://ubuntuforums.org/showthread.php?t=1587462)
A easy way to remove the amount of kernels is to install Ubuntu tweak:
[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

---

