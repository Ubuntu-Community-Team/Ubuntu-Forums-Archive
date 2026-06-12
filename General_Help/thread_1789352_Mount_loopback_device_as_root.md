---
title: "Mount loopback device as root"
date: 2011-06-23
forum: General Help
---

### Post by gizmo720 on 2011-06-23
I am trying to expand my Ubuntu partition into my Windows 7 C: drive, but the win7 partioner will not let me shrink it because of immovable files. Is there anyway for me to but an loopback device in the windows partion, and have Ubuntu boot with that as the root device?

---

### Post by gizmo720 on 2011-06-23
I am going to try doing this through the initrd. However, I tried extracting the files from my current initrd, then copy them into an ext2 file I created (and mounted). However using that as my initrd causes a kernel panic when it cannot mount the root device. The exact same commands in Grub using the original initrd boot properly. 

What is the proper way to construct an initrd image? 
Also, if anyone knows a better way of making a loopback device root, please post that.

---

