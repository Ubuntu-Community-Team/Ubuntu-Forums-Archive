---
title: "New motherboard - Ubuntu won't boot (please help a new girl out!)"
date: 2011-03-08
forum: General Help
---

### Post by emtdan on 2011-03-08
Hey guys-

I just got my laptop back from lenovo with a new motherboard. All of my kernels won't boot - including my recovery drives. WIndows does work which is what I am on. I tried to boot to a live cd and it get to "install ubuntu" then hangs.  I can see my ubuntu partition from windows and just copied everything from that partition.  What should I do!?

---

### Post by Chronon on 2011-03-08
The LiveCD hasn't booted for me for several releases now.  You can find another distro that does boot or try to figure out different boot options that will allow the Ubuntu CD to boot.

I installed an Ubuntu remix of 9.10 and have upgraded since then.  If I need to reinstall I will probably go to Debian.

(I'll just add that it's some peculiarity of my hardware with the LiveCD.  Most people can boot just fine.)

---

### Post by HermanAB on 2011-03-08
Howdy,

The first thing to do, is to defragment Windows, then boot a live CD and partition the disk.  The defragmenting is the easy part, since it is Windows, which you say works.

Your problem then becomes booting the live CD, so you should try the usual kernel switches for startup problems and append to the boot string:
noapic nolapic

When you boot the CD, press an arrow key down to prevent it from booting automatically and read the instructions for modifying the boot string.

It should look somewhat like this:
kernel (hd0,0)/boot/vmlinuz root=/dev/hda1 noapic nolapic

Another oft used kernel switch is acpi=off, but do NOT do that on a laptop as it may overheat and then you need a new motherboard again.  If the above two switches fail to boot the machine, try another distribution, such as Fedora or OpenSuse.

Hope that helps!

---

### Post by emtdan on 2011-03-08
Thanks for the help!

Fortunately, I JUST found this thread
[http://ubuntuforums.org/showthread.php?p=10537439&posted=1#post10537439](http://ubuntuforums.org/showthread.php?p=10537439&posted=1#post10537439)

It worked perfectly!

Thanks for your time!

---

