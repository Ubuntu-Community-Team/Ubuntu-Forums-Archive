---
title: "Two kernel issues"
date: 2006-03-14
forum: General Help
---

### Post by mrbirdy857 on 2006-03-14
Hi,

I have two problems.  First, my machine runs horribly slow when I am running a 2.6 kernel, but fast as it should when running a 2.4 kernel.  Second, I have been trying to compile a 2.4 kernel, but every time get an error that looks like this:

/usr/src/kernel-source-2.4.27/include/asm/processor.h:75: error: array type has incomplete element type
In file included from /usr/src/kernel-source-2.4.27/include/linux/unistd.h:9,
                       from init/main.c:17:

Does anybody have any insight to these issues?

---

### Post by dan_linder on 2006-03-14
For the speed issue, my laptop has a similar problem.  It turns out that my problem was due to how the kernel was handling the HyperThreading in my CPU.  The fix for me was to add "idle=halt" to the boot "kopt=" string in "/boot/grub/menu.lst". In my menu.list file, it is located on line 62.  

My original line looked like this:
# kopt=root=/dev/hda1 ro

Now I have this line:
# kopt=root=/dev/hda1 ro idle=halt

Note, _keep_ the "#" infront of this line.  The "update-grub" script uses them to update the actual kernel strings.  Once you update the file, run "sudo update-grub" and reboot.

Of course if that wasn't your problem, that probably won't help...  :???: 

Dan

---

