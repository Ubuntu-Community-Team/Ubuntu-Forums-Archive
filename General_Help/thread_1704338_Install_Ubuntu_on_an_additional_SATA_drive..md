---
title: "Install Ubuntu on an additional SATA drive."
date: 2011-03-10
forum: General Help
---

### Post by Exzackly on 2011-03-10
I have a Dell XPS 420 with a 500gb SATA drive on which Windows Vista is installed. I also have an additional hard drive that I wish to install for an Ubuntu installation.  Is it possible to create a dual boot system with Windows on the original HD and Ubuntu on the newly installed HD?

Simply put, my computer will have 2 hard drives. The original hard drive has Windows installed. I would like for the second drive to contain the Ubuntu install so that the only thing changed on the original drive is the MBR (I suppose that's how it would work).

Thanks in advance.
Exzackly

---

### Post by bodhi.zazen on 2011-03-10
> **Exzackly said:**
> I have a Dell XPS 420 with a 500gb SATA drive on which Windows Vista is installed. I also have an additional hard drive that I wish to install for an Ubuntu installation.  Is it possible to create a dual boot system with Windows on the original HD and Ubuntu on the newly installed HD?

Simply put, my computer will have 2 hard drives. The original hard drive has Windows installed. I would like for the second drive to contain the Ubuntu install so that the only thing changed on the original drive is the MBR (I suppose that's how it would work).

Thanks in advance.
Exzackly

Should be trivial. Install Ubuntu using the default settings. It is typically when people do not go with the defaults that they run into problems.

Be sure to understand which HD is which in LINUX terminology (Linux does not use C:/ E:/ )

---

### Post by lithopsian on 2011-03-10
Absolutely.  Just look carefully on the install partitioning screen and pick the right disk.

---

### Post by oldfred on 2011-03-10
The one issue grub has is it will default to sda's MBR, unless you tell it otherwise. And the newest version only gives you a choice if you use manual install and create your partitions manually which is recommended anyway.

Lots of detail with screenshots. 
Dual boot 2 drives, windows & Lucid 10.10
[http://members.iinet.net.au/~herman546/p24.html]("http://members.iinet.net.au/%7Eherman546/p24.html")

---

### Post by YesWeCan on 2011-03-10
> **Exzackly said:**
> Simply put, my computer will have 2 hard drives. The original hard drive has Windows installed. I would like for the second drive to contain the Ubuntu install so that the only thing changed on the original drive is the MBR (I suppose that's how it would work).

You ought to put the Ubuntu bootloader on the same drive as Ubuntu. That way your Vista drive remains untouched. This is important because Vista will gag if you apply certain updates and its MBR is not legit. You can still boot Vista from your Ubuntu drive.

In the Ubuntu installer, make sure you click on advanced settings (or something like that) to tell it to put Grub2 on the MBR of the Ubuntu drive. Otherwise it may well default to wiping your Vista MBR.


BTW you can also configure Vista's bootloader to boot your Ubuntu installation. In Vista, just download EasyBCD (free) and tell it to add linux/Grub2 to the menu.

---

