---
title: "Grub shows more two different Ubuntu OS entries. Why?"
date: 2010-09-29
forum: General Help
---

### Post by shiajun on 2010-09-29
Hello everyone,

This is my first post on the forums. Recently I decided to partition my computer to have dual boot into windows and ubuntu. Everything has been working fine but I have a very confusing doubt. When the Grub menu shows up during boot I can see the expected partitions for windows (the OS and a memory test utility installed by DELL) but also not one but two entries for Ubuntu that only differ in name (plus the corresponding recovery mode entry). One says Linux 2.6.32-24 and the other 2.6.32-25. Both of them seem to boot into the same place as far as I can tell when I try either of the entries. I went into the edit mode to see if I spotted any differences and got this:

recordfail
insmod ext2
set root= '(hd0,5)'
search --no-floppy--fs -vvid --set 166a9c40-077a-4dda-83f9-83755a73ca3f
linux /boot/vmlinuz -2.6.32-24 -generic root=UUID=166a9c40-077a-4dda-83f9-83755a73ca3f ro quiet splash
initrd /boot/initrd.img-2.6.32-24 generic

The -25 entry is exactly the same just changing 2.6.32-24 to 2.6.32-25 

There's no problem as is, just that boot menu looks kind of crowded and I'm wondering if I can delete any of the ubuntu entries without killing the computer's boot sequence. Also, if anyone can tell me how the duplication came about I'll also be very grateful so I don't do it again. The only thing I've actually done by myself through the command line so far was an attempt to update the ALSA mixer that I cancelled once the download had started. 

Thanks in advance.

---

### Post by andrewthomas on 2010-09-29
It is showing two different kernels.  

If you want to change how many entries are shown you can install bum.

---

### Post by garvinrick4 on 2010-09-29
If you want to remove kernel go to synaptics type the kernel in and remove.
2 headers and 1 kernel generic. Nice to leave at least 2 in grub menu incase one
does not work properly you got the other one to use.

---

### Post by shiajun on 2010-09-29
Aaah, ok. I get it. Thanks for the quick replies. I think I'll just leave them as it is then. Just on last thing. Always good to have an alternate door for fixes.

---

### Post by jtweaker on 2010-09-29
In case you change your mind, you can use "ubuntu tweak" for easy cleaning of old kernels.its very easy to use and pretty straight forward. just google it :)

---

