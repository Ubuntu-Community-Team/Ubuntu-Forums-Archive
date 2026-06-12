---
title: "Dual booting Windows and Ubuntu, do you share files on the hard drive?"
date: 2011-07-23
forum: General Help
---

### Post by ILuvMontyPython on 2011-07-23
Hi, I am buying a new laptop and am curious about dual booting it. I currently run Ubuntu full time, but will need windows for a few applications. (there are no cross over applications to do this) 

When you put both windows and ubuntu on a computer do you share the hard drive? Meaning would I be able to access all my music in windows and then restart my computer-run ubuntu, would I have access to all the files?

---

### Post by seawolf167 on 2011-07-23
There is a good how-to and information guide [here ]("https://help.ubuntu.com/community/WindowsDualBoot")on dual booting Windows and Ubuntu. Specifically in your case, check out [this ]("https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu")section. Essentially you will install Windows, then reinstall Grub, and update it. 

As for sharing files, your Ubuntu install can read and write to NTFS formatted partitions, but Windows cannot read basically anything but NTFS and FAT. This means that while booted in Ubuntu, you can access, play, edit, etc. **all** your Windows items, but you **cannot **do the reverse.

---

### Post by dirghrabadia on 2011-07-23
You can create a separate NTFS partition that is accessible from both the OS, and store your files on there.

---

### Post by ILuvMontyPython on 2011-07-23
Awesome, thank you!

---

### Post by seawolf167 on 2011-07-23
No problem - unless you have more questions please mark this thread as solved under Thread Tools

---

### Post by Blasphemist on 2011-07-23
First, here is a great tutorial on dual boot of all flavors that includes much other useful information. Thanks to Herman! [http://members.iinet.net.au/~herman546/](http://members.iinet.net.au/~herman546/)

You can set up a partition formatted as ntfs to use for shared music, pictures, documents, etc. This may be more than you are ready to get into but maybe not. Doing the easiest install will result in windows directories for sharing those things, on the windows partition. There is nothing wrong with that.

---

### Post by STPitcher on 2011-07-23
The alternative to dual-boot is Virtual Machines...  Really nifty.  This could be very practical and simpler if you're only using Windows occasionally for one or two simple little applications.

The most obvious Virtual Machine packages are VMware, which is a commercial package and I don't believe there's any free access to it.  I use VirtualBox, which I believe is a Cisco (?) product, but is available free.

With these, you don't have to assign an entire large partition for just a couple of simple applications.  It can use a dynamically allocated, virtual disk, which will use minimal space.  It can also access all your Ubuntu files via a Shared Disk.  Also, you can run your Windows machine and applications simultaneous with your Linux system.

- stp

---

