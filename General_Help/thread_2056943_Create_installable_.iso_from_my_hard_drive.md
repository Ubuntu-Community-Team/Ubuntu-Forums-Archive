---
title: "Create installable .iso from my hard drive"
date: 2012-09-12
forum: General Help
---

### Post by Maro848 on 2012-09-12
Hey guys I have an Ubuntu install in Virtualbox that I have done a lot of work on to make it customized for me, I started the project when I was new to linux and was not yet comfortable with installing it to my hard drive. I was wondering if there was an easy way to take the .vdi image of the virtual hard drive and make an installable (or at least bootable) .iso through the host (win 7) or through the Ubuntu guest itself? I would like to be able to use the customized install on more than just the VM side I want to get it on dedicated hardware so any and all help/ ideas are welcomed and appreciated.

---

### Post by Ubunterrific on 2012-09-12
> **Maro848 said:**
> Hey guys I have an Ubuntu install in Virtualbox that I have done a lot of work on to make it customized for me, I started the project when I was new to linux and was not yet comfortable with installing it to my hard drive. I was wondering if there was an easy way to take the .vdi image of the virtual hard drive and make an installable (or at least bootable) .iso through the host (win 7) or through the Ubuntu guest itself? I would like to be able to use the customized install on more than just the VM side I want to get it on dedicated hardware so any and all help/ ideas are welcomed and appreciated.

 There's a pretty complex looking guide here: [http://www.turnkeylinux.org/blog/convert-vm-iso](http://www.turnkeylinux.org/blog/convert-vm-iso) Interesting. :)

---

### Post by Maro848 on 2012-09-12
Hmmm.... that does look fairly complex, it does assume that the host OS is Ubuntu, which isn't a problem, I can just make a new VM and set the VDI used by it as the one I want to make into a .iso and that should work on getting it so I can follow that guide. So I will give this a look and try it. I would like to know if there is another, possibly simpler way that someone has tried however. I have tried (somewhat naively) to convert my vdi image to a .iso using imgburn. Needless to say it didn't work lol

---

### Post by Maro848 on 2012-09-12
For those that are interested I have so far found a package called remastersys that has allowed me to create a bootable and installable .iso of my vm. I installed remastersys into the vm and created a "backup" .iso so that I can install that exact system on real hardware. I am currenty playing around with the options to create a custom .iso from a fresh one downloaded from Ubuntu.

---

### Post by Ubunterrific on 2012-09-12
> **Maro848 said:**
> For those that are interested I have so far found a package called remastersys that has allowed me to create a bootable and installable .iso of my vm. I installed remastersys into the vm and created a "backup" .iso so that I can install that exact system on real hardware. I am currenty playing around with the options to create a custom .iso from a fresh one downloaded from Ubuntu.

remastersys, you say? I'll have to have a look at that later this week thanx :popcorn:

---

### Post by ezsit on 2012-09-19
I have used remastersys from Ubuntu 7.04 onwards and it has worked wonderfully. However, I have never used it from within a VM. Be sure to visit the homepage [www.remastersys.com](www.remastersys.com) and read the instructions and browse the forum, you will probably get the best answers there. Good luck.

---

