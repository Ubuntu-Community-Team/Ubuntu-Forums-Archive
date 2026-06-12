---
title: "Configuring/Optimizing Dual Core Pentiums"
date: 2006-05-10
forum: General Help
---

### Post by JaceMan on 2006-05-10
Hey everyone... I just got a new computer with a Intel Pentium D 820.  I was wondering if anyone could tell me if I need to do anything special to optimize or configure Ubuntu to take advantage of my dual core processor? :-k 

Thanks in advance!

---

### Post by Gomez Akita on 2006-05-10
I would suggest you need to check if your kernel supports SMP if not I would recompile it with SMP support.

There are others here that know more about linux than me they may have more suggestions.

---

### Post by JaceMan on 2006-05-10
[QUOTE=Gomez Akita]I would suggest you need to check if your kernel supports SMP if not I would recompile it with SMP support.[/QUOTE]

Step 1.  Find out if my kernel supports SMP.
Step 2.  Learn how to recompile kernel. ;)

---

### Post by Gomez Akita on 2006-05-10
open /boot/config.[kernel version] in a text editor and look for the line:

CONFIG_SMP

This will tell you if it is enabled (=y) or not (=n) the whole line may also be remarked out by begining with a #.

You can not enable SMP by editing this file!  there is a very good article in the Howto section that gives the steps for recompiling the kernel.  During the recompile one of the options is to enable SMP support.

---

### Post by ZylGadis on 2006-05-10
In Ubuntu you can very easily see whether your kernel supports smp by opening Synaptic, searching for "kernel", and seeing which exact version of linux-kernel you have. If it says something like linux-kernel-i386-smp, you're fine. If not, install the one that says so, and you'll be fine :) No (re)compilations needed.
You might also consider the i686 versions (smp or not), which are optimized for Intel cpus.
You can check your cpu specifications as recognized by linux by opening a terminal and typing in

cat /proc/cpuinfo

Hope that helps.

---

### Post by JaceMan on 2006-05-11
glitch -- message needs deleted

---

### Post by JaceMan on 2006-05-11
glitch -- message needs deleted

---

### Post by JaceMan on 2006-05-11
glitch -- message needs deleted

---

### Post by JaceMan on 2006-05-11
glitch -- message needs deleted

---

### Post by JaceMan on 2006-05-11
glitch -- message needs deleted

---

### Post by JaceMan on 2006-05-11
glitch -- message needs deleted

---

### Post by JaceMan on 2006-05-11
Thanks Gomez and ZylGadis... this is good information.  I'm sure it will help.  Time to partition the drive, and dual boot my new machine with Windows and Ubuntu.  This will give me 3 computers running Linux.  

Hooray!

---

### Post by JaceMan on 2006-05-12
[QUOTE=ZylGadis]In Ubuntu you can very easily see whether your kernel supports smp by opening Synaptic, searching for "kernel", and seeing which exact version of linux-kernel you have. If it says something like linux-kernel-i386-smp, you're fine. If not, install the one that says so, and you'll be fine :) No (re)compilations needed.
You might also consider the i686 versions (smp or not), which are optimized for Intel cpus.
You can check your cpu specifications as recognized by linux by opening a terminal and typing in

cat /proc/cpuinfo

Hope that helps.[/QUOTE]

Thanks this worked like a charm, based upon what Gomez had to say...

[quote=Gomez Akita]open /boot/config.[kernel version] in a text editor and look for the line:

CONFIG_SMP
[/quote]

After I used synaptic with your advice and rebooted, my new kernel is rocking with SMP support enabled.

Now I have one more stupid question.

After installing Ubuntu, then installing updates, then the new kernel -- well now when I boot up Grub offers me about 6 choices for various kernel images to boot into Ubuntu with.  How do I best modify the boot menu to rid myself of the old choices?

---

### Post by mcduck on 2006-05-12
[QUOTE=JaceMan]Thanks this worked like a charm, based upon what Gomez had to say...



After I used synaptic with your advice and rebooted, my new kernel is rocking with SMP support enabled.

Now I have one more stupid question.

After installing Ubuntu, then installing updates, then the new kernel -- well now when I boot up Grub offers me about 6 choices for various kernel images to boot into Ubuntu with.  How do I best modify the boot menu to rid myself of the old choices?[/QUOTE]
You can just uninstall the older kernels with Synaptic, and those entries will be removed from GRUB :)

Two tips: When you install kenel other than the default, don't install any specific kernel version, but a metapackage like linux-686 ot linux-K7. Thhese metapackages depend on latest kernel version, kernel headers and restricted modules. This way you'll get everything else needed, and also automatic updates for your kernel. And when the kernel gets updated, don't remove the old one until you have booted the new one, and you are sure that everything works fine..

---

### Post by JaceMan on 2006-05-12
Thanks Mr. McDuck.  Old 386 Kernels and Kernel Images marked for removal, reboot, and voila!  Grub now says, "Look JaceMan you can either boot into Unbuntu optimized for Intel multi-processors or Windows Media Center but that's it.  It's one or the other Jack!"

To which I reply, "The name is Jace not Jack, but thanks.  That is what I was after anyway."  :)

---

### Post by ZylGadis on 2006-05-12
You have an odd grub. Mine says nothing of the sort, it just spits out a menu :D
Glad it worked.

---

### Post by Hoffmann on 2006-05-12
[QUOTE=JaceMan]Hey everyone... I just got a new computer with a Intel Pentium D 820.  I was wondering if anyone could tell me if I need to do anything special to optimize or configure Ubuntu to take advantage of my dual core processor? :-k 

Thanks in advance![/QUOTE]

I have the same type of processor you have. Take a look on the link below:

[http://www.ubuntuforums.org/showthread.php?t=85917](http://www.ubuntuforums.org/showthread.php?t=85917)

All you need to do is just to install the smp kernel:

```
sudo apt-get install linux-686-smp
```

After that, reboot your machine, and use the new installed kernel. In the terminal do this:

```
top
```

and type 1. This way, you will see that both of your CPUs are working and running (Cpu0 and Cpu1). In other words, your will be using your dual core with all the power. It is amazing such a power. 

One more hint: DO NOT INSTALL Ubuntu-64 bits on your core dual machine. I did that before, and it didn't work very well. Several features are missed such as flashplayer, etc. There is the option of chroot, but in my opinion that is not good. I mean, I would need to creat a 32-bit enviroment on the 64 one. In my opinion, this would be "ridiculous"; I would be using 32-bits, instead of 64-bits several times.... A lot of work need to be done yet (Windows 64bits and Linux 64bits cases). All you need is just Ubuntu-32 bits and the kernel I mentioned above.

I hope this help.
Hoffmann

---

