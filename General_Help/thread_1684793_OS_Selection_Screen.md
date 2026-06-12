---
title: "OS Selection Screen"
date: 2011-02-09
forum: General Help
---

### Post by fallofshadows on 2011-02-09
I'm running a dual booted ubuntu 10.10 64 bit with windows 7 64 bit. 

You know the screen where it tells you to select your operating system? I have two questions about it.

One: Is there a way to make it look better? Some Macs here at my college are dual booted with windows/macOSX, and there's a nice pretty screen that helps you choose which one you want to use. Like, it's graphic, has pictures involving each OS symbol, etc. I Just think it looks nice, and I would love to make my computer do that instead of just showing me an ugly list of OSes.

Two: There are a few different copies of linux that show up in the list, and it's gotten bigger over time. It's like

Linux Ubuntu (bunch of numbers)
Linux Ubuntu- Safe mode (bunch of numbers)
Linux Ubuntu (different numbers)
Linux Ubuntu- Safe mode (same different numbers)
Linux Ubuntu (even more numbers)
Linux Ubuntu- Safe mode (again)
Windows 7

Is there a way to just break it down to the top Linux Ubuntu (that's the one I use to log in) and windows 7? I just want to make this screen look nicer.

Thanks!

---

### Post by matt_symes on 2011-02-09
Hi

You can customise the grub2 bootloader screen

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

and there is burg

[http://www.ubuntugeek.com/how-to-change-your-grub-loader-view-using-burg.html](http://www.ubuntugeek.com/how-to-change-your-grub-loader-view-using-burg.html)

The easiest way to remove older kernels is to use ubuntu tweak

```
sudo apt-get install ubuntu-tweak
```

Package cleaner->clean kernel

I would suggest keeping two Linux kernels. The newest and the second to newest.

Kind regards

---

### Post by quadproc on 2011-02-09
> **fallofshadows said:**
> 
One: Is there a way to make it look better? 
The grub-pc program gives you a lot of flexibility in appearance.  Check out [https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto) especially the section titled Boot splash images.
> 
Is there a way to just break it down to the top Linux Ubuntu (that's the one I use to log in) and windows 7?Yes.  There are a couple of ways to remove entries from the bootable list: one is to make the unwanted kernels non-executable; that is, to change their permissions.  The other is to actually remove the unwanted kernels.  You can use apt-get remove or Synaptic to do the removal.  CAUTION! Do not remove your running kernel!  That would make the system useless.

Whichever method you choose, you need to run update-grub afterwards so that the changes will be recognized.

It is usually wise to keep at least two working OS versions on a system, just in case something happens to the version that you usually use - you can then fall back to the previous version.

quadproc

---

### Post by fallofshadows on 2011-02-12
Thanks for the help guys!

One question before I go and delete kernels (because I don't want to mess this one up lol). This may sound stupid, but the most recent kernels would be 2.6.35-24-generic, right? The confusing thing is, there's also 2.6.35-24, without the "generic" on the end. What sorts of things do I want to delete here? I'm gonna attach a screenshot, since that should be more clear.

---

### Post by techunit on 2011-02-12
You might want to look into "Burg" (Grub backwards)

It gives you a GUI selection tool. This guide is pretty good.

[http://www.omgubuntu.co.uk/2010/06/get-animated-themed-icon-only-grub-menu-using-burg-now-simple-to-use/](http://www.omgubuntu.co.uk/2010/06/get-animated-themed-icon-only-grub-menu-using-burg-now-simple-to-use/)

---

