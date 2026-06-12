---
title: "Completely and permanently disabling plymouth splashes ?"
date: 2010-12-15
forum: General Help
---

### Post by scotty64 on 2010-12-15
Is there a way to completely and permanently disable the startup and shutdown plymouth splashscreens. Setting nosplash in GRUB only disables the GRUB splash but not the plymouth stuff.

---

### Post by tredegar on 2010-12-15
Please read [this]("https://help.ubuntu.com/community/Grub2") to understand what is going on.

Then remove **splash** and **quiet** from the options on the **GRUB_CMDLINE_LINUX_DEFAULT="...."** line in **/etc/default/grub**

Then run (as root) **update-grub**

Reboot.

All should be well, and you'll get a load of kernel text scrolling past (but I like that).

---

### Post by scotty64 on 2010-12-16
> **tredegar said:**
> Please read [this]("https://help.ubuntu.com/community/Grub2") to understand what is going on.

As I said, I have done that already. The system is still switching to framebuffer and shows the Ubuntu/Kubuntu splash with the growing dots/line at both startup and shutdown. This is the one I want to get rid of.

---

### Post by tredegar on 2010-12-16
Strange.

Please paste the output of **cat /proc/cmdline** here.

---

### Post by Krytarik on 2010-12-16
> **tredegar said:**
> Strange.

Please paste the output of **cat /proc/cmdline** here.
And by the way, the content of /etc/default/grub also please.

---

### Post by scotty64 on 2010-12-17
I solved the problem so far: I was used to put "nosplash" in the grub configuration, but plymouth seems to ignore that. Having nothing in the linux command line options in /etc/default/grub does the job.
However, the framebuffer is still initialized and thats what I do not want. The reason is that I am running this Kubuntu in a VirtualBox guest and I can see that the fb-initialization sometimes messes up the X-start resulting in an Ubuntu low graphics mode.

---

### Post by BlueSpecial on 2010-12-17
> **scotty64 said:**
> I solved the problem so far: I was used to put "nosplash" in the grub configuration, but plymouth seems to ignore that. Having nothing in the linux command line options in /etc/default/grub does the job.
However, the framebuffer is still initialized and thats what I do not want. The reason is that I am running this Kubuntu in a VirtualBox guest and I can see that the fb-initialization sometimes messes up the X-start resulting in an Ubuntu low graphics mode.

I think (not sure!) that adding **_quiet _**to the grub prevents the scrolling text to show...

You can also install "Start Up Manager" from Software Center and set boot logo time to 0... this prevents logo from showing as well.

---

### Post by scotty64 on 2010-12-17
I just found the way to disable all the framebuffer stuff and get a smooth console:

edit /etc/modprobe.d/blacklist-framebuffer.conf and add the folling line:

blacklist vga16fb

The next reboot will be without fb (but X is still working fine)

---

### Post by tredegar on 2010-12-17
After the reboot, are your  VTs on ctrl-alt F1-F6 still working?
You might miss them, unless you can easily ssh into your PC from another one.

---

### Post by scotty64 on 2010-12-17
> **tredegar said:**
> After the reboot, are your  VTs on ctrl-alt F1-F6 still working?
You might miss them, unless you can easily ssh into your PC from another one.

All VTs are working fine and F7 brings me back to X.

---

