---
title: "How do i upgrade kernel to 2.6.30"
date: 2009-06-28
forum: General Help
---

### Post by geekyhawkes on 2009-06-28
I have been told i need to upgrade my kernel in Kubuntu 801 from 2.6.27 to 2.6.30 to get my DVB-T card working.  

The machine is running Linux MCE so i cannot just upgrade to 9.04 but have not been able to find a guide here or via google that covers the upgrade (and i dont know my way around well enough to guess!).

Any help well recieved.

Thanks.

---

### Post by cmost on 2009-06-28
Well, you could go through the arduous task of compiling your own kernel, or, you can take whichever version you like from here:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

I'm using the 2.6.29.5 stable kernel.  You'll note that a release candidate for 2.6.31 is available but I strongly discourage you from using RCs with low numbers.

You'll need to download the headers for your CPU architecture (i386 for 32bit systems or amd64 for 64 bit systems), the generic headers (denoted "all") and the Linux image (three files total.)  The source file is optional but if you download it, choose the correct architecture.

Save the files to a folder, then enter that folder and open a Terminal.  Issue the following command to install the new kernel and headers:

sudo dpkg -i *.deb

You'll need to reboot.  If all is working well, then you can uninstall the old kernel.  Note:  If you're using ATI or Nvidia graphics then you'll need to recompile its kernel module.  The same might be true for your wireless card or other hardware.

Good luck!

---

### Post by fooman on 2009-06-28
i used the following to upgrade my jaunty 9.04 to the 2.6.30 kernel about a week ago...so far,  so good!  :p

[http://www.ramoonus.nl/2009/06/10/linux-kernel-2-6-30-installation-guide-for-ubuntu-and-debian-linux/](http://www.ramoonus.nl/2009/06/10/linux-kernel-2-6-30-installation-guide-for-ubuntu-and-debian-linux/)

---

### Post by geekyhawkes on 2009-06-29
Great stuff thanks guys.  I think i will leave the RC just now, im still learning some of the ins/outs of linux and i think the rc is a bit too sporty for me just now!

---

