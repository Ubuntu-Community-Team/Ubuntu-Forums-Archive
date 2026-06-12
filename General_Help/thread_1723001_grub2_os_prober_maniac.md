---
title: "grub2 os_prober maniac"
date: 2011-04-06
forum: General Help
---

### Post by nuttygraphics on 2011-04-06
I usually have had one boot partition and two or more os. All of them could be booted from the single boot partition from a single instance of grub.

Since grub2 and the os_prober, I get the weird problem, that every os is combined with every kernel from the boot partition. For example: I have a ubuntu 10.04 lts x64 as a main working system. It has 2 kernel updates. So, there are 3 kernels for this os. Then I have a ubuntu 10.10 x86 on another partition (lvm actually, but I guess it makes no difference). The 10.10 was installed just for tryout. There is only the default kernel. Now, when update-grub2'ing from the 10.04 system, which happens after each kernel update and also if I use the startupmanager. I get entries for the kernel of the 10.10 system. Selecting those entries fails with a binfmt-464c problem, which indicates a mix up between x64 and x86 code. 
I guess, if the 10.10 had been a x64 system, then it would have booted, but subtile errors would appear, because the kernel might still not be equivalent.

My actual question is: Was my initial idea of using a single boot partition with multiple os such a bad idea? How should I do it?

thanks for any idea!

Ingo

---

### Post by techunit on 2011-04-06
I can only tell you there are many reasons for staying as close to the dual booting instructions but I see no reason why a boot partition is so bad.

---

### Post by nuttygraphics on 2011-04-06
I am not sure I understand completely. Are there some "dual boot instructions" I should follow? Where can I read about it?

---

### Post by oldfred on 2011-04-06
You really should not share any system partitions. You can share swap if you do not hibernate. /boot is tiny so you are not saving any real space. The only reasons to have a separate /boot would be an old system with the 137GB boot limit or RAID or LVM which may work better with boot outside of the special partitions.

Herman on advantages/disadvantages of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

---

