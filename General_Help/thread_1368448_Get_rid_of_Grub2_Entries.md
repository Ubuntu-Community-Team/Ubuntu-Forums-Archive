---
title: "Get rid of Grub2 Entries"
date: 2009-12-30
forum: General Help
---

### Post by Beastlicker on 2009-12-30
Hey. I installed and updated Ubuntu. After I updated, I noticed that I had two kernel options to boot up with. I ran ```
sudo update-grub
```, and they still remain. Here are the results I get when I run that command


```
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1

```

Is there anyway to remove the 2.6.31-14 kernel, or is it natural for it to be there?

---

### Post by Leppie on 2009-12-30
go to System>Administration>Synaptic
remove all kernels your not using anymore, this will remove the entries from grub as well. if they still show up after reboot, you can always update the grub.cfg by running:
```
$sudo update-grub
```

---

### Post by Beastlicker on 2009-12-30
Would I also get rid of the headers for the specific kernel?

---

### Post by Leppie on 2009-12-30
yes, those usually are only required if you need to do stuff like compiling kernel modules, etc.
since you're no longer going to use that kernel, you don't need the headers anymore either.

---

