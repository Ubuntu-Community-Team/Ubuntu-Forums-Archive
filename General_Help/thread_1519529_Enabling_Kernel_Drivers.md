---
title: "Enabling Kernel Drivers"
date: 2010-06-28
forum: General Help
---

### Post by beastrace91 on 2010-06-28
Howdy All,

I am playing around with [Longene]("http://www.longene.org/en/index.php") on Ubuntu 10.04 and the issue I am having is that their default kernel packages do not have support for my wifi card (I'd like support for both atheros and intel wifi) or the synaptic touch pad on my laptop.

I've never really tinkered with compiling a custom kernel before and I cannot seem to locate where these drivers are in the configuration menu so when I compile from source they can be enabled - any suggestions?

~Jeff

---

### Post by justleen on 2010-06-28
If you have to compile the driver from source, you should have to recompile the kernel.
You end up with a .ko file (after compilation) which you should place in /lib/modules/../.  Once in there, run "depmod -a" and "modprobe yourdriverfilename"

---

### Post by beastrace91 on 2010-06-28
> **justleen said:**
> If you have to compile the driver from source, you should have to recompile the kernel.
You end up with a .ko file (after compilation) which you should place in /lib/modules/../.  Once in there, run "depmod -a" and "modprobe yourdriverfilename"

Yes... What I am asking is where I can find the option to enable support for the pieces of hardware I list when compile the entire kernel. I know the Linux kernel supports them as many distributions have these pieces of hardware working OOTB (such as Ubuntu's generic kernel).

In short - when I am in menuconfig before I compile which submenu do I want to look in to toggle on support?

~Jeff

---

### Post by justleen on 2010-06-28
That, I wouldn't know. 
It would involve adding to source of the driver to the kernel source, then running the make-config. Somewhere under net, I would assume.

I was trying to say, if you can get away with just compiling the module, go for that. Since then you dont have to recompile the whole kernel.

---

### Post by beastrace91 on 2010-06-28
In case anyone else is wondering I got a fairly good answer over on the [LQ message boards]("http://www.linuxquestions.org/questions/linux-hardware-18/enabling-kernel-drivers-816799/#post4017227").

> **zordrak said:**
> The guide in my sig will run you through the process of compiling a custom kernel and adding features to an existing configuration, however it is written for Slackware which is simple by design. I cannot speak for Ubuntu or Maemo. In the least it will give you an overview of the general process in its simplest form which may help your understanding.

With regard to locating the specific drivers, you should only need to find the exact name of the driver you need, and then use the search function in menuconfig to locate it.

For example, if what you need is the ath9k atheros driver, when you enter menuconfig, just type a forward-slash (/) and enter ath9k, and you get this result:



Which shows you the location and dependencies of both the ath9k driver and it's associated debugging module.

~Jeff

---

### Post by dino99 on 2010-06-28
> **beastrace91 said:**
> In case anyone else is wondering I got a fairly good answer over on the [LQ message boards]("http://www.linuxquestions.org/questions/linux-hardware-18/enabling-kernel-drivers-816799/#post4017227").



~Jeff

Thanks, you have found an interesting project, it might be followed by many users and if you succeed with testing, a new howto thread would help a lot.

[http://www.longene.org/en/aboutproject.php](http://www.longene.org/en/aboutproject.php)

---

### Post by beastrace91 on 2010-06-28
Thats the plan. Once I get it up and rolling with a kernel that has wifi and touch pad support I will be writing up a HOWTO for any else that want to try it (also planning on posting pre-compiled packages with the kernel)

~Jeff

---

