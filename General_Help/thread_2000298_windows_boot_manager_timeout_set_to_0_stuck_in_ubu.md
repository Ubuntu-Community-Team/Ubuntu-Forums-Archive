---
title: "windows boot manager timeout set to 0 stuck in ubuntu"
date: 2012-06-09
forum: General Help
---

### Post by Runoono on 2012-06-09
I`m stuck in Ubuntu because my Windows boot manager timeout is set to zero
don`t get me wrong I like Ubuntu but there are somethings I just need Windows for...

---

### Post by matt_symes on 2012-06-09
Hi

Is this a WUBI or partition installation ?

Assuming a partition install with GRUB installed, you should be able to get the grub boot menu by pressing the shift key at boot.

You can change the timeout by editing the file /etc/default/grub and changing the GRUB_TIMEOUT= value and then running

```
sudo update-grub
```

If it's a WUBI install then i cannot help as i have never used it.

Kind regards

---

### Post by Runoono on 2012-06-09
> **matt_symes said:**
> Hi

Is this a WUBI or partition installation ?

Assuming a partition install with GRUB installed, you should be able to get the grub boot menu by pressing the shift key at boot.

You can change the timeout by editing the file /etc/default/grub and changing the GRUB_TIMEOUT= value and then running

```
sudo update-grub
```If it's a WUBI install then i cannot help as i have never used it.

Kind regards


I used WUBI

well
at least do you know how I can merge my other windows installation with grub
(Its on another partition)

---

### Post by bcbc on 2012-06-09
You need a windows repair CD, boot to a repair prompt and run:
```
bcdedit /timeout 10
```

Windows usually uses a single boot partition when you install more than one release. So it probably won't help to boot your other windows from grub. Also wubi is set to ignore other windows partitions (even if it is separate). Part of the reason was to stop users thinking they could boot windows from grub and setting the timeout to zero.

Anyways - a windows repair cd should do the trick.

PS if it's windows XP, you can just edit the boot.ini, but it sounds like you have Vista/7 (they require the repair cd)

---

### Post by Runoono on 2012-06-11
thanks trying it now

---

### Post by wfu on 2012-09-07
there is actually a way... after boot into ubuntu, you actually can find a file called BCD in the System/Boot directory.  Copy it out and open it on another windows machine with tool like EasyBCD, edit the timeout value, save it and copy it back to overwrite the original BCD file, then you're done.:p 

There might be linux tool that can edit the BCD file, but I didn't dig further...

Hope it's helpful.

---

