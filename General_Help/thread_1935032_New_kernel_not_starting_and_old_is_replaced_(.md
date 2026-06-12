---
title: "New kernel not starting and old is replaced :("
date: 2012-03-03
forum: General Help
---

### Post by c2tarun on 2012-03-03
Hi friends

I downloaded and installed a new kernel according to this page, [http://www.cyberciti.biz/tips/compiling-linux-kernel-26.html](http://www.cyberciti.biz/tips/compiling-linux-kernel-26.html)

Now from my grub menu the default option I am getting is of that kernel and when I am opening that kernel I am getting a blank black screen. To start my ubuntu I have to go to previous kernels option and then select one from there. Is there any way to restore my old kernel.

One more question, I want to learn some kernel development, I was reading book 'Linux Kernel Development' by Robert Love. To practice I want to install and start a new kernel in such a way that my old Ubuntu installation doesn't get affected. Can anyone please suggest a good kernel installation tutorial?

Thanks

---

### Post by pbrane on 2012-03-03
Unfortunately you probably need to reverse the process by which you installed the new kernel.

I would recommend that you have a look at this page for future kernel installs:
[https://wiki.ubuntu.com/KernelTeam/GitKernelBuild]("https://wiki.ubuntu.com/KernelTeam/GitKernelBuild")

I use this method and it works great. I can install a custom kernel using **dpkg** and remove it using **apt-get**. You don't have to clone the kernel if you don't want to. I usually use the latest stable kernel from *kernel.org*.

---

### Post by c2tarun on 2012-03-03
> **pbrane said:**
> Unfortunately you probably need to reverse the process by which you installed the new kernel.

I would recommend that you have a look at this page for future kernel installs:
[https://wiki.ubuntu.com/KernelTeam/GitKernelBuild]("https://wiki.ubuntu.com/KernelTeam/GitKernelBuild")

I use this method and it works great. I can install a custom kernel using **dpkg** and remove it using **apt-get**. You don't have to clone the kernel if you don't want to. I usually use the latest stable kernel from *kernel.org*.



I will definitely use your method :) but first I need to reverse what I did :( can you please help me with it?

---

### Post by pbrane on 2012-03-03
I have never installed a kernel using that method so I don't know how much help I can be. If you followed the guide exactly then you have installed the 2.6.25 kernel. You *may* be able to remove the kernel by replacing  *make install* with *make uninstall* and *make module_install* with *make module_uninstall*. You will still have to edit menu.lst and remove the entry you added.

**Be very careful in following these directions. You need to think before you delete anything. Basically you want to look at the guide you used to install the kernel and work in reverse to un-install it.**

Maybe these steps can help guide you. **Use these steps as a GUIDE ONLY, removing the wrong system files can wreck your system!** If you installed a kernel other than 2.6.25 replace the 2.6.25 in these *steps* with the kernel version you installed.

1. remove or comment out the entry you added to menu.lst.

2. run **update-grub** in a terminal. After this you should be able to reboot to the original kernel.

2. look in /lib/modules/ for a 2.6.25 directory and if found remove it.

3. look in /boot and remove any files with 2.6.25 in them, the **System-map-2.6.25, config-2.6.25, vmlinuz-2.6.25, and initrd-img-2.6.25** files.

---

### Post by c2tarun on 2012-03-03
> **pbrane said:**
> I have never installed a kernel using that method so I don't know how much help I can be. If you followed the guide exactly then you have installed the 2.6.25 kernel. You *may* be able to remove the kernel by replacing  *make install* with *make uninstall* and *make module_install* with *make module_uninstall*. You will still have to edit menu.lst and remove the entry you added.

**Be very careful in following these directions. You need to think before you delete anything. Basically you want to look at the guide you used to install the kernel and work in reverse to un-install it.**

Maybe these steps can help guide you. **Use these steps as a GUIDE ONLY, removing the wrong system files can wreck your system!** If you installed a kernel other than 2.6.25 replace the 2.6.25 in these *steps* with the kernel version you installed.

1. remove or comment out the entry you added to menu.lst.

2. run **update-grub** in a terminal. After this you should be able to reboot to the original kernel.

2. look in /lib/modules/ for a 2.6.25 directory and if found remove it.

3. look in /boot and remove any files with 2.6.25 in them, the **System-map-2.6.25, config-2.6.25, vmlinuz-2.6.25, and initrd-img-2.6.25** files.


I tried installing kernel according to this link[https://wiki.ubuntu.com/KernelTeam/GitKernelBuild](https://wiki.ubuntu.com/KernelTeam/GitKernelBuild) but no luck :( I am still getting black screen. Any suggestions?

---

### Post by pbrane on 2012-03-05
Sorry, if you are following the guide exactly it should work. Make sure you are not getting any errors. I assume you have removed the first kernel you installed.

---

### Post by Neill_R on 2012-03-05
Do a Ctrl-Alt-F2 and login in at the prompt.

then do 

sudo /etc/init.d/gdm stop

startx

does this help?

---

