---
title: "After update ubuntu 10.4 won't boot"
date: 2010-08-10
forum: General Help
---

### Post by Brii on 2010-08-10
I'm not sure what updates I installed as it did it automatically and I was surfing the Internet. But I start up my computer again, grub is fine, press enter at Ubuntu but the I'm not welcomed by my splashscreen but rather a terminal like interface that flashes about 6 times and then the screen goes black

So I think the update must have screwed with something to do with the graphics. How can I fix this using Ubuntu recovery mode?

Thanks. 

Any more info will be provided as asked :)

P.S. I'm writing this on my iPod so excuse the spelling mistakes, if any

---

### Post by mal on 2010-08-10
Brii,

If the update included a new kernel, it may not be playing nice with your graphics card.  The simplest approach might be to select the previous kernel at the grub boot screen and then uninstall the new kernel once you get back to the desktop.

Mal

---

### Post by Brii on 2010-08-10
Thanks for the reply, but how do I uninstall the kernel or activate the old on from the terminal?

---

### Post by Brii on 2010-08-10
> **mal said:**
> Brii,

If the update included a new kernel, it may not be playing nice with your graphics card.  The simplest approach might be to select the previous kernel at the grub boot screen and then uninstall the new kernel once you get back to the desktop.

Mal

I went into the grub configure file and saw vmlinux-2.6.32-24-generic

I ls'd that directory and saw that there's about 4 files like that but with smaller numbers at th end. I thought this wa the kernel so I shortened the number to match the other files. But no luck. It booted the same as before

---

### Post by mal on 2010-08-10
Brii,

You should be able to select a kernel at start-up from the initial grub menu that appears when you boot the computer.  If this is not displayed, press the escape key during boot and the menu should appear.

I don't think it's a good idea to edit the filenames in the grub configuration file.  You can configure grub to default to a different kernel by changing the line "GRUB_DEFAULT=0" in the file /etc/default/grub.  For example if you change this to "GRUB_DEFAULT=2" it will boot the next oldest kernal (3rd line on the boot menu).  I think you will need to run "sudo update-grub" after making this change.

You can also remove the unwanted kernel using Synaptic (from the System/Administration menu).

Hope this helps.

Mal

---

### Post by Brii on 2010-08-10
> **mal said:**
> Brii,

You should be able to select a kernel at start-up from the initial grub menu that appears when you boot the computer.  If this is not displayed, press the escape key during boot and the menu should appear.

I don't think it's a good idea to edit the filenames in the grub configuration file.  You can configure grub to default to a different kernel by changing the line "GRUB_DEFAULT=0" in the file /etc/default/grub.  For example if you change this to "GRUB_DEFAULT=2" it will boot the next oldest kernal (3rd line on the boot menu).  I think you will need to run "sudo update-grub" after making this change.

You can also remove the unwanted kernel using Synaptic (from the System/Administration menu).

Hope this helps.

Mal

Damn, nothing worked. Editing the default didn't work either.

---

### Post by tcopeland on 2010-08-10
It's probably your **xserver** that did it. Are you using proprietary drivers? In that case, the new version of xorg probably isn't compatible with your proprietary drivers. You'll need to rollback your xserver. I have forgotten how to do this but i'm sure someone else can. And that someone may be Google.

---

### Post by Brii on 2010-08-10
I ran the package recovery in recovery mode, it didn't fix anything, but I saw this 
```

Directory: usr/src/psb-kernel-source-4.42.0 does not exist

```

Is this my problem?

Thanks.

---

### Post by Brii on 2010-08-11
> **tcopeland said:**
> It's probably your **xserver** that did it. Are you using proprietary drivers? In that case, the new version of xorg probably isn't compatible with your proprietary drivers. You'll need to rollback your xserver. I have forgotten how to do this but i'm sure someone else can. And that someone may be Google.

My graphics card isn't supported. I'm not using any real drivers for it. 

I forget but if GMA500 is a type of graphics card nthats the one I have

---

### Post by Brii on 2010-08-11
Okay I found out that my problem is indeed  the fact that the kernel updated

I do have a gma500 and the kernell is 2.6.32-24-generic 

How do I downgrade? I have internet access in the command line if that helps.

---

### Post by mal on 2010-08-11
Brii,

I suggest you enter the following from the command line:

```
sudo apt-get remove linux-image-2.6.32-24-generic && reboot
```

This should remove the new kernel and reboot the computer on the previous kernel.  (I am assuming that the previous kernel is still installed and in good working order.)

Mal

---

### Post by Brii on 2010-08-11
> **mal said:**
> Brii,

I suggest you enter the following from the command line:

```
sudo apt-get remove linux-image-2.6.32-24-generic && reboot
```

This should remove the new kernel and reboot the computer on the previous kernel.  (I am assuming that the previous kernel is still installed and in good working order.)

Mal
Damn. Still getting the same thing. I boot into ubuntu and it flashes then goes black. ><

Also FYI Now I'm in kernel 2.6.32-22 

Thanks a bunch. I really appriciate it.

---

### Post by jbernardo on 2010-08-11
First - boot into recovery, and run "aptitude purge psb-kernel-source". It should remove the buggy old version. Also remove /etc/x11/xorg.conf (but do a backup first, poulsbo-config should install it but always play safe).
Second - reinstall the latest kernel. I am on 2.6.32-24, and it works well on my 1101HA.
Third - reinstall the packages - "sudo apt-get install psb-kernel-source"; if not enough, do also a "sudo apt-get install poulsbo-driver-2d poulsbo-driver-3d poulsbo-config".

If it still fails, please post the errors you get when installing the packages.

Also, as a last resource you can do:
```
sudo ppa-purge ppa:gma500/ppa && sudo apt-get update
sudo add-apt-repository ppa:gma500/ppa && sudo apt-get update
sudo apt-get install poulsbo-driver-2d poulsbo-driver-3d poulsbo-config

```

---

### Post by Brii on 2010-08-11
> **jbernardo said:**
> First - boot into recovery, and run "aptitude purge psb-kernel-source". It should remove the buggy old version. Also remove /etc/x11/xorg.conf (but do a backup first, poulsbo-config should install it but always play safe).
Second - reinstall the latest kernel. I am on 2.6.32-24, and it works well on my 1101HA.
Third - reinstall the packages - "sudo apt-get install psb-kernel-source"; if not enough, do also a "sudo apt-get install poulsbo-driver-2d poulsbo-driver-3d poulsbo-config".

If it still fails, please post the errors you get when installing the packages.

Also, as a last resource you can do:
```
sudo ppa-purge ppa:gma500/ppa && sudo apt-get update
sudo add-apt-repository ppa:gma500/ppa && sudo apt-get update
sudo apt-get install poulsbo-driver-2d poulsbo-driver-3d poulsbo-config

```


Hey, it worked! Thanks a lot to everyone who helped. I learned a lot. =D

Thanks again.

---

### Post by bvhoesel on 2010-09-19
This did the trick for me also. Thanks a lot.

---

### Post by ilab888 on 2010-11-14
Hi,

I have exactly the sane problem, i.e. I was naive and downloaded the new kernel through the update mamager. Now I can not get into any recovery facility because grub is not displayed even I press ESC. The recovery mode does not take me out of the blinking screen. What can I do!??

Thank you
Leonard
:mad:

---

