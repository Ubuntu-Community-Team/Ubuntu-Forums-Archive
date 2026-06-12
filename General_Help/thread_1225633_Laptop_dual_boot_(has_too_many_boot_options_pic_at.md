---
title: "Laptop dual boot (has too many boot options *pic attached)"
date: 2009-07-28
forum: General Help
---

### Post by jramosjr on 2009-07-28
Ok I have an HP 6515b. I Installed XP Pro (work) and Ubuntu 9.04.
It used to boot fine with two boot options. But after an update in the past, and another update today it now has 6 different Ubuntu boot-into options. Please see the pic below. How do I get rid of the 4 unwanted?
thanks in advance.

[IMG]http://i26.tinypic.com/2qnmsmw.jpg[/IMG]

---

### Post by munky99999 on 2009-07-28
```
sudo gedit /boot/grub/menu.lst
```

Then put # infront of the boots you dont need... as in the older kernels.

Such that:

title Ubuntu, kernel 2.6.20-15-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=fccafcc7-d7cc-4594-9459-a8f0db7b9f7f ro quiet splash
initrd /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

Becomes

#title Ubuntu, kernel 2.6.20-15-generic
#root (hd0,0)
#kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=fccafcc7-d7cc-4594-9459-a8f0db7b9f7f ro quiet splash
#initrd /boot/initrd.img-2.6.20-15-generic
#quiet
#savedefault

---

### Post by nmaster on 2009-07-28
are those older kernels taking up disk space?  shouldn't the OP try to remove them rather than just change the boot options that are displayed.

---

### Post by jramosjr on 2009-07-28
Awesome! That worked!! Thnx again! You are the man! or woman! :)

Any reason why it did this? Is one better than the other?

---

### Post by munky99999 on 2009-07-28
> **neal.m.master said:**
> are those older kernels taking up disk space?  shouldn't the OP try to remove them rather than just change the boot options that are displayed.
the kernels are probably about 10megs each. Considering the cost of hard drives today... not something to worry about for size.

Compare that to the potential positive effects of having good kernels sitting around waiting for a disaster to happen.

Also considering the chance of causing problems by accidentally removing the kernel you shouldnt have.

Best option is to simply remove them from view. As opposed to remove them enirely.

---

### Post by munky99999 on 2009-07-28
> **jramosjr said:**
> Awesome! That worked!! Thnx again! You are the man! or woman! :)

Any reason why it did this? Is one better than the other?
Well every kernel. Different drivers and all kinds of things can change. New bugs could pop up. Which means it would be best to have it so that... you update to a new kernel. You use that new one. The boot menu still shows the old ones... which ought to be working fine. If there's a problem... it's easy enough just to load the other kernel.

---

### Post by louieb on 2009-07-28
> are those older kernels taking up disk space?  ...> Any reason why it did this? Is one better than the other?     :Dyou get use to it.  I don't see the menu long enough to bother.  Two pages on my desktop running Hardy 8.04. 

Probably will get around to cleaning it up when I do a fresh install of the next LTS release.

---

