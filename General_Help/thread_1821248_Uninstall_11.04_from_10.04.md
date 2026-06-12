---
title: "Uninstall 11.04 from 10.04"
date: 2011-08-08
forum: General Help
---

### Post by gustokonyan on 2011-08-08
Hi,

I originally have ubuntu 10.04 installed. Then I installed Ubuntu 11.04 "alongside 10.04" (usb installer).  Now i want to uninstall 11.04.

They say just remove the 11.04 partition. But i think that might cause a problem because when I boot my laptop, it uses the 11.04 boot loader. I am afraid that if i remove the 11.04 partition, i will have no boot loader at all?? I want to be sure..

How do I go around this?


Thanks ..

---

### Post by Basher101 on 2011-08-08
By default GRUB is written to your /dev/sda (your hard disk, or to be more percise your MBR), **_not_** your partiton (/dev/sda1 or /dev/sda2). So removing the partition would only leave the **entry** in GRUB. When you deleted the partition and rebooted into 10.04, simply run the command in the terminal ```
sudo update-grub
``` to remove the entry. Post your outcome if it worked

---

### Post by gustokonyan on 2011-08-08
Hi, thank you. That makes sense. I will try this as soon as I get back home..

I only assumed that my 11.04 boot loader would persist because, when I tried to change my boot settings using start-up manager on my 10.04, nothing happened. I edited grub config files on it, updated, restarted, nothing happened too.

But when I tried start-up manager on 11.04, it worked.

.. so i assumed they have separate boot loaders, and 11.04's boot loader is the one being used? I will highly appreciate if anyone can clarify more on this.

I am a new ubuntu fan :D

---

### Post by Basher101 on 2011-08-08
Yes, 11.04 uses Grub 2 version 1.99

---

### Post by gustokonyan on 2011-08-08
> **Basher101 said:**
> Yes, 11.04 uses Grub 2 version 1.99

Uhmm ok. So, is it still safe to just remove the 11.04 partition despite of this? I want to be extra sure hehe, i can't afford to lose my 10.04. :)

---

### Post by Basher101 on 2011-08-08
even if you SHOULD be able to manage (somehow...) to delete grub as well, put in the live cd...you can restore grub with only a few commands, there are many step by step threads on how to do this

---

### Post by gustokonyan on 2011-08-08
> **Basher101 said:**
> even if you SHOULD be able to manage (somehow...) to delete grub as well, put in the live cd...you can restore grub with only a few commands, there are many step by step threads on how to do this

Great! but i do not have a live cd. I used the usb installer. I assume it can do the same job?

---

### Post by Basher101 on 2011-08-08
Its still a Live CD. You just use other media (like a DVD instead of a CD) and in your case its a USB :KS

---

### Post by gustokonyan on 2011-08-08
> **Basher101 said:**
> Its still a Live CD. You just use other media (like a DVD instead of a CD) and in your case its a USB :KS

Thank you Basher101! :)

---

### Post by Basher101 on 2011-08-08
Thanks appreciated :KS

---

