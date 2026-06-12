---
title: "VirtualBox USB issue."
date: 2010-05-27
forum: General Help
---

### Post by s.v.z on 2010-05-27
Hi everyone. I`ve got WinXP in VirtualBox on my Ubuntu 10.04. I wish to connect my phone via USB and work with it from Windows. Is there a way to do it?

---

### Post by ownaginatious on 2010-05-27
Ya, VirtualBox has support built directly into it for attaching USB devices to the virtual machine. I believe you need to enable it somewhere in the machine's settings when it's turned off.

It's under something like "USB 2.0 support". That should let you attach USB devices to the virtual machine while it's running from the lower right hand side of the virtual machine's window.

---

### Post by s.v.z on 2010-05-27
Have found the USB tab on some screenshots on the net, but not in my VM properties =( Guess I`ll have to try another version of Virtual box. =)

---

### Post by ownaginatious on 2010-05-27
Oh right, as far as I remember the version of virtual box included in the Ubuntu repository does not have USB support for some reason.

If you're using x64 try this: [http://download.virtualbox.org/virtualbox/3.2.0/virtualbox-3.2_3.2.0-61806~Ubuntu~lucid_amd64.deb](http://download.virtualbox.org/virtualbox/3.2.0/virtualbox-3.2_3.2.0-61806~Ubuntu~lucid_amd64.deb)

If you're on an 32-bit system, try this: [http://download.virtualbox.org/virtualbox/3.2.0/virtualbox-3.2_3.2.0-61806~Ubuntu~lucid_i386.deb](http://download.virtualbox.org/virtualbox/3.2.0/virtualbox-3.2_3.2.0-61806~Ubuntu~lucid_i386.deb)

---

### Post by phr33k-dc on 2010-05-27
u need to use the non-free version of virtual box as far as i know

---

### Post by Zemblan on 2010-05-27
I believe the USB connectivity is not available with the open source version of VBox. You'll have to install the Personal Use and Evaluation version, which has some closed source additions, and can be found on the Virtual Box website.

---

### Post by s.v.z on 2010-05-27
OK, I`ll give it a try. Thanks.

---

### Post by dustinmarlowe56 on 2010-05-27
S.V.Z,

you may also run into the problem of being able to see your usb's but not be able to attach them to the virtual machine. i ran into this problem myself but it is a simple fix. just run sudo VirtualBox and it should let you connect them.

---

