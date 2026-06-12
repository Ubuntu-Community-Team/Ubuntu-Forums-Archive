---
title: "compiling source code"
date: 2011-03-14
forum: General Help
---

### Post by vivek.pandey on 2011-03-14
hey everyone

i just downloaded linux kernel 2.6.38 source code just for studying  and was going through it . i have doubts 

1)if  i compile and run any of the files there ,(using gcc)will it be causing any problem to the existing one which is already running?
2) can i compile and install the entire source code along with my existing kernels without putting myself into trouble of some sort?
3)if i can install it...what when i will boot into this new kernel after starting my laptop? will it be safe to do that? 
thanx a lot

---

### Post by lithopsian on 2011-03-14
1. No.  Compile away.
2. Yes.  You can have as many kernels as you can be bothered to mess with.  You can even install multiple builds of the same kernel version by changing the extra EXTRAVERSION string at the top of the main Makefile.
3. When you have successfully installed and built a new kernel, you can put it in your Grub menu (or Grub2 will put it there for you) and then you can choose to boot into it if you like.  Make sure you do update-initramfs for the new kernel before you try to boot to it.  If it fails, then just reboot to the old kernel and try to fix it.

---

### Post by vivek.pandey on 2011-03-14
thanx for your reply....but how can i go about finding bugs or something in the code. i  mean all of them get compiled without any error (obviously) using gcc ?

---

