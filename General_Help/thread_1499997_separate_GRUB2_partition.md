---
title: "separate GRUB2 partition?"
date: 2010-06-02
forum: General Help
---

### Post by pythonscript on 2010-06-02
I'm going to be installing multiple Linux distributions on my workstation, so I'm looking to set up a separate partition for GRUB2. What files do I need to copy over? I know I need:

/etc/grub.d/*
/etc/default/grub

But can I just copy these directory trees over? As in, should I put *grub-partition*/etc/grub.d/

and just copy the files right into it? How would I do this?

---

### Post by arrange on 2010-06-02
Have you looked at Herman's tutorial?
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition)

---

### Post by wojox on 2010-06-02
Just install your diffrent distro's manually and at the very end [reinstall from LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

---

