---
title: "How to install windows 7 from ubuntu please help?"
date: 2009-08-04
forum: General Help
---

### Post by bphicks123 on 2009-08-04
Hello everyone i am currently running ubuntu.

Is there a way to install Windows7 while running ubuntu?

I dont want to have to burn it to a disc, i just want to click install from the file. I have heard that this wont work since ubuntu does not use .exe files. What can i do?

---

### Post by bphicks123 on 2009-08-04
anyone have any ideas?

---

### Post by warp99 on 2009-08-04
Short answer is no, but you can either dual boot Windows 7 or run it virtualized using Vmware or Virtualbox. Here are some help guides:

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

[https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)

[https://help.ubuntu.com/community/VMware/Player](https://help.ubuntu.com/community/VMware/Player)

---

### Post by hyperdude111 on 2009-08-04
No you can not just run the file, ubuntu and windows are completley different operating systems no windows executable will run on uubuntu (without emulation) and vice-verser. There are other methods although for you to try to test windows 7.

Virtual Machine - Easy to use and set up, only requires an iso no disk burning required but it is supported. It features a complete OS install into a virtual disk file stored on your hard drive. Virtual machines support all x86 and x64 operating systems as long as you have sufficient system resources.

Your choices are of Virtualbox of VMware. 

Virtualbox is free, easy to use and supports many features.
VMware it a pay to use app, it is also very good missing some Vbox features but having others however it is not worth the pricetag.

This image shows how virtualbox works (althought its not windows 7 it will still work) 
[IMG]http://www.blogcdn.com/www.downloadsquad.com/media/2008/02/virtualbox-ubuntu.jpg[/IMG]

---

### Post by bphicks123 on 2009-08-04
what emulator can i use to run the .exe file, and just install windows?

---

### Post by hyperdude111 on 2009-08-04
> **bphicks123 said:**
> what emulator can i use to run the .exe file, and just install windows?

Not possible. WINE can run .exe's but the installer for win7 replaces windows operating system files which are not present in ubuntu or the wine library.

---

### Post by bphicks123 on 2009-08-04
ok,
can i do this then: run windows virtually, then completely install windows 7 from there?

or will it not let me?

---

### Post by hyperdude111 on 2009-08-04
> **bphicks123 said:**
> ok,
can i do this then: run windows virtually, then completely install windows 7 from there?

or will it not let me?

Yes, that is the whole point of visualization software. You can install windows in a virtual machine and it is kept separate from your ubuntu system.

---

