---
title: "Installing Kernels via Update Manager"
date: 2010-05-05
forum: General Help
---

### Post by bill_p on 2010-05-05
Since upgrading to 10.04 (Beta 1, kernel 2.6.32-16), Update Manager does not update the kernel when a new one is available. It gets the headers, but does not install the kernel, as it did when new kernel updates were available in 9.10. See this [thread]("http://ubuntuforums.org/showthread.php?t=1456694") which originally was posted for Lucid testing. 
 
When a new kernel package was recently made available in Update Manager, 2.6.32-22, the new kernel was again not installed. It just downloaded the headers. By running sudo apt-get install linux-image-2.6.32-22-generic, I upgraded the default kernel.
 
My question is, do I have have to run sudo apt-get install linux-image-2.6.32-xx-generic each time there's a new kernel available, or should I be able to do this through Update Manager.

---

