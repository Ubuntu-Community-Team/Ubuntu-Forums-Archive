---
title: "Bootloader/MBR: help required"
date: 2011-01-21
forum: General Help
---

### Post by Ecip on 2011-01-21
ok, ubuntu... you got me. i'm so happy with it I got rid of my windows 7 installation on this laptop.. only a few things to do. let me show you guys:

> roger@roger-Satellite-A100:~$ sudo update-grub 
[sudo] password for roger:  
Generating grub.cfg ... 
Found linux image: /boot/vmlinuz-2.6.35-24-generic 
Found initrd image: /boot/initrd.img-2.6.35-24-generic 
Found linux image: /boot/vmlinuz-2.6.35-23-generic 
Found initrd image: /boot/initrd.img-2.6.35-23-generic 
Found linux image: /boot/vmlinuz-2.6.35-22-generic 
Found initrd image: /boot/initrd.img-2.6.35-22-generic 
Found memtest86+ image: /boot/memtest86+.bin 
Found Windows 7 (loader) on /dev/sda1 
done1) as you can see, for some reason there are a few images of linux that are listed when I update grub.. i'm not sure wtf is going on with that.. i only have one installation of ubuntu on this computer. i assume its probably from updates as linux comes out with new versions over time... how do I remove these extra ones and only leave /boot/vmlinuz-2.6.35-24-generic?

2) as you can also see, the windows partition is still showing up, part due to the boot manager being installed on a 100MB partition (it just worked out that way, win 7 set up a system only partition, and thats where ubuntu set up the MBR. i will leave this as is, doesnt bother me). How do I make the boot loader boot directly into linux, without showing a list of operating systems?


Thanks to the great help available and the search feature, i managed to get everything except the above two problems fixed up.

*edit: you know, thinking about it, as long as i can get the bootloader to just boot directly into linux, thats really all i would want. i'm sure eventually the hard drive will die on this laptop or i'll need to reinstall ubuntu for whatever reason. lol

---

### Post by lindsay7 on 2011-01-21
Install Ubuntu Tweak and you can clean up the list of start up kernels from there and also do other clean ups for your system. Install Startup Manager and set the time out to 1 and it will act like there is only one os on your computer.

There are other ways to do this but this is easy and gives you other options for your system that you my want to use anyway.

---

### Post by Ecip on 2011-01-21
i'll give it a try, thanks.

---

