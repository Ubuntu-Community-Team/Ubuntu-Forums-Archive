---
title: "Will not wake up"
date: 2009-10-31
forum: General Help
---

### Post by Digikid on 2009-10-31
Running the latest Ubuntu on a HP Touchsmart TX2 1224CA Laptop.  When I close the lid it goes to sleep as programmed....however it refuses to wake up.  The lights all go on and it appears to wake up but no video or sound whatsoever.

Linux newbie here so be** POLITE** and **THROUGH**.

Thank You.

---

### Post by grandtoubab on 2009-10-31
take-off battery, unplug power cord, tak-on battery, plug-on power cord and go

---

### Post by Digikid on 2009-10-31
> **grandtoubab said:**
> take-off battery, unplug power cord, tak-on battery, plug-on power cord and go

ok now I am asking for USEFUL help...

Pretty much told me to reboot....which is NOT the issue here.

---

### Post by Ayuthia on 2009-11-02
I still have the i8042.reset boot parameter in my menu.lst but I am not for sure if it is still needed or not.  It was mainly for the keyboard and mouse, but if your laptop goes into suspend mode, I think you either need to move the mouse or press a key to bring up the password screen (at least that is how it is for Kubuntu).  If your keyboard and mouse are not working then this could be the problem.

You can try it by going into /boot/grub/menu.lst:
```
gksu gedit /boot/grub/menu.lst
```or use kate instead of gedit for Kubuntu and look for a line that looks like:
```
title           Kubuntu 9.10, kernel 2.6.31-14-generic
root (hd0,7)
kernel          /boot/vmlinuz-2.6.31-14-generic root=UUID=abcde84325-b72e-4de1-bd24-39666d5a231e ro vga=803 splash
initrd          /boot/initrd.img-2.6.31-14-generic
quiet

```and change the kernel line to read
```
kernel          /boot/vmlinuz-2.6.31-14-generic root=UUID=abcde84325-b72e-4de1-bd24-39666d5a231e ro vga=803 i8042.reset splash
```

You might also try the alsa force-reboot to see if your sound comes back.  This is based on the information from this [link]("http://ubuntuforums.org/showthread.php?t=1304273&highlight=tx2+sound").

---

### Post by P4man on 2009-11-02
> **Ayuthia said:**
> 
You can try it by going into /boot/grub/menu.lst:.

Note these instructions wont work with ubuntu 9.10 as it uses grub 2. Perhaps the original poster can clarify first which version of ubuntu he is using.

Also, when you try to wake the system, after a few seconds try this:
control+alt+F1
this *may* give you a full screen terminal. If it does try
control+alt+F7
to return to the gui. If these commands do nothing, let us know.

---

### Post by RonB123123 on 2009-11-10
Same issue. I'm running Ubuntu 9.10 on an HP Pavilion dv6000. I'll try the commands you suggested P4man and let everyone know. Besides work arounds, does anyone know the progress Ubuntu developers or the kernel developers have made?

---

### Post by P4man on 2009-11-10
> **RonB123123 said:**
>  does anyone know the progress Ubuntu developers or the kernel developers have made?

Unless this is filed and confirmed as a bug in ubuntu's launchpad or on kernel.org bugzilla, probably none. Then again its kind of impossible to know for me if the problem is in ubuntu ,the kernel, videodrivers or your bios.

If you got an nvidia card in that machine you could also try this trick:
[http://ubuntuforums.org/showpost.php?p=3825488&postcount=2](http://ubuntuforums.org/showpost.php?p=3825488&postcount=2)

---

### Post by Ayuthia on 2009-11-10
> **P4man said:**
> Note these instructions wont work with ubuntu 9.10 as it uses grub 2. Perhaps the original poster can clarify first which version of ubuntu he is using.



Thanks for pointing this out.  I forgot about the change to grub 2.  I have been using Gentoo as my main OS and I am still using grub.

---

