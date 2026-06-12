---
title: "linux 686-smp"
date: 2006-05-19
forum: General Help
---

### Post by physcsdrk on 2006-05-19
I was following a howto from the ubuntu wiki ([BinaryDriverHowto/ATI]("https://wiki.ubuntu.com/BinaryDriverHowto/ATI?highlight=%28binary%29"))

and I typed in:
```
sudo apt-get install linux-686-smp
```
and restarted.

I think I just had linux-686 before but the howto said do linux-686-smp for p4's that support hyperthreading.  Now I cannot get a ps/2 keyboard or mouse to work but I can get a usb mouse to work.  I don't have a usb keyboard.  Does anyone know of anything I can do to get it working?  Or if not that, then how do I uninstall the linux-686-smp.  (if that is a dumb question, sorry.  I am a total newb)

Thanks for any help in advance.

---

### Post by xXx 0wn3d xXx on 2006-05-19
To uninstall, type:

> sudo apt-get remove linux-686-smp

_Make sure you are NOT using the kernel while you are removing it_. Try re-installing and see if you get the same result. Sorry that I can't help with the keyboard/mouse. Did it work with previous kernels ?

---

### Post by physcsdrk on 2006-05-19
I booted into the regular 686 kernel and typed what you said.  However, upon restarting my computer I still see the 686-smp option in Grub and it is still the default.  I haven't tried booting into it or anything.  

I thought maybe I didn't remove it right so I tried removing it again and it tells me its not installed.  So I definately removed it.  
Is there anyway for a.) grub to not show the 686-smp, or b.) to change the default in grub.  

While I am on the topic, grub shows two versions of xp but only one of the options work....how do I remove the other option?

---

### Post by ctgray on 2006-05-20
you can edit your /boot/grub/menu.lst

It is pretty well documented

---

