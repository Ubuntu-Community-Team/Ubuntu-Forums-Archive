---
title: "Uninstalling Windows 7 Starter Edition"
date: 2012-02-24
forum: General Help
---

### Post by Candace001 on 2012-02-24
Hi There,
I am very green to Ubuntu. I just installed Ubuntu 11.04 with the Wubi Installer on a Toshiba netbook running Windows 7 Starter edition. I was wondering if and how to uninstall the Windows 7 Starter Edition that came on the netbook. The netbook has always been painfully slow and am thinking just running Ubuntu would make it a little faster. If anyone can give me a step by step on how to uninstall Windows I would appreciate it.:D
Thanks

---

### Post by elliotn on 2012-02-24
> **Candace001 said:**
> Hi There,
I am very green to Ubuntu. I just installed Ubuntu 11.04 with the Wubi Installer on a Toshiba netbook running Windows 7 Starter edition. I was wondering if and how to uninstall the Windows 7 Starter Edition that came on the netbook. The netbook has always been painfully slow and am thinking just running Ubuntu would make it a little faster. If anyone can give me a step by step on how to uninstall Windows I would appreciate it.:D
Thanks

boot with the ubuntu liveCD and proceed to install, when u reach the part that makes u choose which partition to use just choose whole drive, ubuntu will wipe windows and install ubuntu, alternatively u can use gparted to wipe the drive, run sudo gparted

---

### Post by Candace001 on 2012-02-24
Would that I could, but it's a netbook without a  dvd drive. Is there another way to do this with out using a flash drive. Could I uninstall Windows 7 from Ubuntu. Also where on Ubuntu do I find the OS on the hard drive?

---

### Post by PhantomTurtle on 2012-02-24
I read somewhere that its possible to boot off the iso stored on your Windows partition. This method uses Magic ISO Maker to mount the ISO when you computer boots ([Look here]("http://www.magiciso.com/tutorials/miso-makebootablecd.htm")). I have not tried this method but its worth a shot. Just make sure to shrink you Windows partition before you do. Then just install Ubuntu to the unpartitioned space. Remember you cannot delete the Windows partition in the Ubuntu installer since that's where the iso is. When you are done you can just Delete the Windows partition in Ubuntu or leave it alone. Again I have never tried this myself so I am not entirely sure that it will work.

---

### Post by Rebelli0us on 2012-02-24
> **Candace001 said:**
> Would that I could, but it's a netbook without a  dvd drive. Is there another way to do this with out using a flash drive. Could I uninstall Windows 7 from Ubuntu. Also where on Ubuntu do I find the OS on the hard drive?

You can install Ubuntu from a USB flash drive (using Startup Disk Creator or ImageWriter). Then you can install Win7 in a virtual machine (using Virtual Box).

---

### Post by Hylas de Niall on 2012-02-24
If OP installs Ubu on the whole drive, the recovery partition and thus Win7 licence goes up in smoke.

7 Starter is a nasty piece of work, the EULA prohibits even changing the dektop wallpaper! In my experience it's worth paying the extra £50 for the anytime upgrade key which turns it into Home Premium ...which, even with the bells and whistles actually runs faster than (or at very least as fast) as Starter edition.

---

### Post by forrestcupp on 2012-02-24
> **Rebelli0us said:**
> You can install Ubuntu from a USB flash drive (using Startup Disk Creator or ImageWriter). Then you can install Win7 in a virtual machine (using Virtual Box).

Right. The download page on ubuntu.com tells you exactly what to do to create a bootable USB. That's going to be your best bet.

---

### Post by elliotn on 2012-02-24
> **Candace001 said:**
> Would that I could, but it's a netbook without a  dvd drive. Is there another way to do this with out using a flash drive. Could I uninstall Windows 7 from Ubuntu. Also where on Ubuntu do I find the OS on the hard drive?
if I understand correctly, u want to keep the WUBI install but remove Win7! no u can't find the ubuntu OS on your drive as it was installed inside windows. your best bet is to to try this tutorial from this link
[http://agnipulse.com/2011/08/install-ubuntu-hard-disk/](http://agnipulse.com/2011/08/install-ubuntu-hard-disk/) 

good luck

---

### Post by husnos on 2012-02-24
> **Candace001 said:**
> Hi There,
I am very green to Ubuntu. I just installed Ubuntu 11.04 with the Wubi Installer on a Toshiba netbook running Windows 7 Starter edition. I was wondering if and how to uninstall the Windows 7 Starter Edition that came on the netbook. The netbook has always been painfully slow and am thinking just running Ubuntu would make it a little faster. If anyone can give me a step by step on how to uninstall Windows I would appreciate it.:D
Thanks

the reason starter edition is painfully slow is because of restrictions on the system resources. It is meant to give you a feeling of the system so that you buy the full one later. You can google many articles talking about its limitations.

So, it is useless to keep for permanent use.

---

### Post by Candace001 on 2012-02-25
Thanks all.  I ended up formatting a flash drive to be bootable, loading on Jolicloud instead.  It seems to be working fine.  I did a clean install of Joli.  Now I just have to figure out how Joli works.lol  It's a lot faster, but there are a few things that work different than a full OS does.  It's all in the learning.:)  Windows 7 starter is really crap. I think this new OS will be much better.
Cheers!

---

