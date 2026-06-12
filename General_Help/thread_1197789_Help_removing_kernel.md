---
title: "Help removing kernel"
date: 2009-06-26
forum: General Help
---

### Post by cottfcfan on 2009-06-26
I installed kernel 2.6.29 to try and help my ATI Video playback.
However its not yet compatible with the ATI proprietary driver.
Now I cant get rid of it.
Its not in packages in Synaptic. And everytime I edit my boot/grub/menu.lst and delete it,
it is there again after i reboot.
How do i delete it for good??

---

### Post by loomsen on 2009-06-26
Keep it that way, but run

```

sudo update-grub
```

after you saved and closed your menu.lst

---

### Post by cottfcfan on 2009-06-26
Thanks for your reply.
 It was when i ran sudo update-grub that it put the kernel back in the menu.lst???

---

### Post by loomsen on 2009-06-26
No.

You have to run update-grub if you change menu.lst due to debians automagic...

It will look into /boot and generate an entry for each kernel-initrd.img combo found.

If you wanna remove your kernel, you have to use dpkg, apt or any other packagemanager. Unnecessary to mention you can't remove it while online with that kernel.

Reboot, boot into any other kernel, then uninstall everything (searching for the verision should give you the packages installed, for 2.6.29-4 for example

```
dpkg -l | grep 2.6.29-4
```

remove the packages listed, dpkg -r, aptitude remove or something similar. update-grub should then be called by a kernel postinstaller script.
So, simply boot into your old kernel and remove the new one.

Seems like that is what I misunderstood above, thought you already removed it. (i915? you have KMS then enabled by default... has to work if so. Try again passing vga=<your mode> to your kernel line.

Make it look something like this (ignore the UUID)
[[img]http://www.ubuntu-pics.de/thumb/17260/screenshot_019_8LVwkP.png[/img]](http://www.ubuntu-pics.de/bild/17260/screenshot_019_8LVwkP.png)

NOTE: vga=0x365 is MY resolution, so, unless you have a 1440x900 display this won't work for you. 
You may use 
vga=ask
to be prompted upon boot and choose from a list.

---

### Post by cottfcfan on 2009-06-26
Loomsen,  

I`m booted into another kernel, but its not allowing me to remove the 2.6.29 kernel.
I can see them in the boot menu but theres no option to delete them.
And everytime i delete them from the menu.lst, and run Update-grub, it finds the 2.6.29 kernel and puts it back again!

---

### Post by cottfcfan on 2009-06-26
SOLVED!!!!

Thanks for your help Loomsen.

I had to open the boot file as root, before it allowed me to delete the kernels.
Now its back to normal.

---

