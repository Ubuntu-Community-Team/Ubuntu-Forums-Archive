---
title: "Ubuntu Extremely Slow"
date: 2012-07-27
forum: General Help
---

### Post by Parkman123 on 2012-07-27
I am using 12.04 LTS on my HP Laptop, Specs are,   AMD A8 Quad Core with AMD Radeon Graphics and 6GB Ram, I am not using it inside of Windows using a virtualization program, it is booting up on its own, and basically Ubuntu is really slow, just like when you click on "system setting" for example, it will take 5 minutes just to open up, and then everything inside of it is really slow, same with basically everything, it just is extremely slow! Any help would be awesome because I want to do some android ROM developing, so linux is really helpful! 

Thanks!

---

### Post by techvish81 on 2012-07-27
> **Parkman123 said:**
> I am using 12.04 LTS on my HP Laptop, Specs are,   AMD A8 Quad Core with AMD Radeon Graphics and 6GB Ram, I am not using it inside of Windows using a virtualization program, it is booting up on its own, and basically Ubuntu is really slow, just like when you click on "system setting" for example, it will take 5 minutes just to open up, and then everything inside of it is really slow, same with basically everything, it just is extremely slow! Any help would be awesome because I want to do some android ROM developing, so linux is really helpful! 

Thanks!

your system hardware seems to be newer, i would recommend to download and install latest kernel to see if it works, from the below link.

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.4-precise/]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.4-precise/")

if there is any problem after installing this kernel,  you can boot to the original kernel by pressing shift while booting and selecting previous linux versions from the grub menu.

---

### Post by Parkman123 on 2012-07-27
> **techvish81 said:**
> your system hardware seems to be newer, i would recommend to download and install latest kernel to see if it works, from the below link.

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.4-precise/]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.4-precise/")

if there is any problem after installing this kernel,  you can boot to the original kernel by pressing shift while booting and selecting previous linux versions from the grub menu.




Ok thanks! I really am not sure, but if I install the kernel, can I still boot into windows? Sorry! I have no idea, and thanks again!

---

### Post by techvish81 on 2012-07-27
yes. ofcourse, even if something goes weird, you can just boot from previous kernel, (as told above) and remove the kernel you installed.

---

### Post by Parkman123 on 2012-07-27
> **techvish81 said:**
> yes. ofcourse, even if something goes weird, you can just boot from previous kernel, (as told above) and remove the kernel you installed.



Great thanks a lot! Just making sure that the kernel had nothing to do with windows!

---

