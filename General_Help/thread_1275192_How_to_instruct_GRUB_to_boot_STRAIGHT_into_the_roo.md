---
title: "How to instruct GRUB to boot STRAIGHT into the root shell"
date: 2009-09-25
forum: General Help
---

### Post by ichudov on 2009-09-25
I had a trouble yesterday. After a motherboard/CPU upgrade, my old network interface eth0 ceased to exist and instead, eth1 appeared. Because the configuration file /etc/network/interfaces referred to eth0, the boot process was permanently stuck on "Configuring Network Interfaces". I could not even log on.

Attempting to do "recovery mode" ended up stuck for the same reason. 

Here's what I want to find out: How can I instruct GRUB/kernel to boot into /bin/sh RIGHT AFTER MOUNTING THE ROOT FILESYSTEM. 

That is, I want to fully bypass initscripts after mounting root filesystem. In Fedora, I could say init=/bin/sh and it worked.

So, how can I get into the root shell right after kernel initializes and root filesystem is mounted?

Please note: I want to get an answer to my question how to get into root shell right after boot. I am NOT interested in other questions like whether it is a good idea, or how to do other things that are not related to my question, as well as philosophical questions about computer security.  

Thank you.

---

### Post by Liolikas on 2009-09-25
kinda hacky but try to add option: root=
It will fail for sure and yoo should end up in busybox

---

### Post by ichudov on 2009-09-25
> **Liolikas said:**
> kinda hacky but try to add option: root=
It will fail for sure and yoo should end up in busybox

I am sorry, but I do not want to be in Busybox. 

I hope that my original request was clear: I am NOT looking for answers suggesting anything other than what I wanted originally, which is to go into root shell afer mounting the root filesystem.

---

### Post by ichudov on 2009-09-25
I just found out from a USENET reply that the following works:

* Reboot and press ESC at the GRUB prompt, to go into GRUB menu
* Press 'e' to edit the kernel selection that you want
* Select a second line in the kernel selection and press 'e' again
* Remove stuff such as "ro quiet splash" and append "rw init=/bin/bash"
* Press ESC to go back

press 'b' to boot, you should drop into root shell. 

I tested this on a Ubuntu Hardy server edition. I will try it later on Ubuntu Jaunty desktop edition to see if it works, which is what I expect. Then I will mark this thread as solved.

Thanks

---

