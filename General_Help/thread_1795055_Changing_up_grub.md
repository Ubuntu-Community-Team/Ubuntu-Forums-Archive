---
title: "Changing up grub"
date: 2011-07-02
forum: General Help
---

### Post by temecula on 2011-07-02
I am currently doing a tri-boot (using refit) with Linux, Windows, and OS X.  I was wondering if it was possible to change up the boot loader for Linux.  I basically wanted grub to not pop-up and just boot the default version of Ubuntu. Also the boot loader comes up with the options to boot Windows and OS X and I was wondering if it would be possible to remove those from the list as well? Thanks.

---

### Post by wildmanne39 on 2011-07-02
> **temecula said:**
> I am currently doing a tri-boot (using refit) with Linux, Windows, and OS X.  I was wondering if it was possible to change up the boot loader for Linux.  I basically wanted grub to not pop-up and just boot the default version of Ubuntu. Also the boot loader comes up with the options to boot Windows and OS X and I was wondering if it would be possible to remove those from the list as well? Thanks.Hi, you can do it but if you make it boot straight to ubuntu then you will not be able to boot the other operating systems, the same if you remove them from the grub.

---

### Post by temecula on 2011-07-02
Are you saying that if I remove OSs from the grub then rEFIt would not be able to boot those as well?

---

### Post by grahammechanical on 2011-07-02
I am assuming that you know what you are doing. I do not know what you are doing but may I suggest that you install Grub Customizer. Under Preferences you can tell GRUB to look for other operating systems. Or, in your case, not to look for other operating systems. You can also set it to show the menu or not and you can set the timeout.

I do not know if this will do what you want but I do know the Grub Customizer is a very good utility that makes changing the way GRUB works very easy.

Regards.

---

### Post by wildmanne39 on 2011-07-02
> **temecula said:**
> Are you saying that if I remove OSs from the grub then rEFIt would not be able to boot those as well?
Hi, I am not sure about refit I have never heard of it, but in almost all cases if someone does what you are trying to do they mess grub up. Grub Customizer is a very easy way to work with grub, I did not mention it earlier because given what you want to do it is also very dangerous. It is possible since you are using another program to boot with that it will work the way you want it too.

---

