---
title: "Install 64-bits version and use 32-bits packages"
date: 2012-05-22
forum: General Help
---

### Post by Shiryu on 2012-05-22
My new computer will support 64-bits OS, but I do not use applications that uses more than 1 GB of RAM alone.
I want to install the 64-bits Kubuntu, but I want to use the 32-bits version of the common applications, such as Firefox, Open/Libre Office, Java Virtual Machine and GCC (32-bits output).
Can I do it with 64-bits Kubuntu or should I install the 32-bits Kubuntu?

---

### Post by PhantomTurtle on 2012-05-22
I would go for 64-bit. It is still possible to run 32-bit software in it. You have several options. Option 1 - install a 32-bit version of Ubuntu in a virtual machine, using virtualbox, vmware, etc. Option 2 - A 32-bit chroot. Option 3 - Installation of 32-bit compatibility libraries (ia32-libs or Multiarch support). Read more about those here - [https://help.ubuntu.com/community/32bit_and_64bit]("https://help.ubuntu.com/community/32bit_and_64bit") (scroll down all the way to the bottom of the page).

---

### Post by grahammechanical on 2012-05-22
I would say that 64bit Ubuntu or Kubuntu will install 64bit versions of any default program if those 64bit versions are in the repositories. This will happen when you install the OS.

The only thing that you need to use a 64bit OS is a 64bit CPU. The amount of RAM is only a factor if you have 4GB or more RAM. A 32bit Ubuntu will run on a 64bit CPU and the installation of the OS will notice if there is 4GB or more RAM and install a pae version of the kernel so that all the RAM can be accessed. But it will not be as efficient as the 64bit Ubuntu and this is because the ability to access more than 4GB of RAM is built in and not put as an extension. Which is what happens with the pae kernel.

Why do you think that it is better to run 32bit programs on a 64bit OS? If you really want to run 32bit programs then install the 32bit OS.

Regards.

---

