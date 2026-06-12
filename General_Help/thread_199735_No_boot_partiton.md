---
title: "No boot partiton"
date: 2006-06-19
forum: General Help
---

### Post by jonathanm on 2006-06-19
Hi, please help, i have accidentaly formatted my /boot partition with my kernel image on it. i was using grub to dual boot winxp and ubuntu and managed to split my swap into two partitions and have made another boot partition. I have also managed to load grub onto it and can boot into windows. I tried copying the kernel from the live cd but this has failed. Any suggestions as to how i can get the kernel back without reinstalling ubuntu? The /boot folder (symlink) is also pointing to the wrong place. Am i ok to delete this and put another symlink in because it doesnt dhow it as a symlink (arrow) in nautilus

Thanks,
Jonathan

PS this has also been posted in the breezy section because that is what i run but i didnt know if i would get better response from here as ai dont think that it is release specific

---

### Post by Rui Pais on 2006-06-19
hi,

there at least 2 ways of dealing with this.

the quick one i'm not sure if it works but it deserves a trial. You have made half of it.

Mount your ubuntu hd partition.
Copy the kernel (vmlinuz-xxxxxxxxx) from the livecd to the new /boot on HD **and** what the directory /lib/modules/version_of_kernel_livecd to your mounted ubuntu /lib/modules/.
Add the need lines to grub menu and try to boot with that one. Then is easy to use synaptic or apt to reinstall your deleted kernel.

If that fails you need the vmlinuz file inside linux-image-xxx.deb of your deleted kernel version. The only kernel stuff from /boot that is really needed is exactly the kernel file. Modules are inside the directories i mentioned above. 

You can download the deb from here:
[http://archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/]("http://archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/")
be carefull with version numbers, the need to mach!

You can open deb file with fille-roler and simply extract the vmlinuz file (inside data.tar.gz file inside deb archive) 

hope that help.
(Post if something was not clear)

---

