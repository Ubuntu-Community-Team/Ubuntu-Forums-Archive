---
title: "HELP - installation of ubuntu from external hdd not booting properly"
date: 2011-01-02
forum: General Help
---

### Post by starion on 2011-01-02
hello ! i need your help.....i have an external hdd to which i hav installed ubuntu....however instead of booting into ubuntu, my computer boots into the grub prompt...then i thought i'll boot off the external hdd on my friend's pc....so on his pc it boots fine, ubuntu runs fine on his pc from my external hdd....but it just wint start on my pc, it gets into grub prompt.....i wanna know how to fix it..PLZ HELP PS: my pc is much better than my friends - and yeah my bios supports booting off of the external hdd via usb. Also, i have taken care that the MBR is written to my external HDD and not hd0

---

### Post by WlaadDyaab on 2011-01-02
I don't know if this would be helpful or not but when I leave the USB (from external hard drive) plugged into my laptop, I also can't even get to the grub menu, it shows some codes repeating themselves over and over again and my laptop doesn't start and I have to manually switch "off" then "on" my laptop

So I just started to unplug the external hard drive's USB cable from the laptop as soon as I restart or switch it off, and once I am on the Ubuntu desktop I plug the USB cable and use the external hard drive normally

I hope that was helpful:neutral:

---

### Post by starion on 2011-01-02
> **WlaadDyaab said:**
> I don't know if this would be helpful or not but when I leave the USB (from external hard drive) plugged into my laptop, I also can't even get to the grub menu, it shows some codes repeating themselves over and over again and my laptop doesn't start and I have to manually switch "off" then "on" my laptop

So I just started to unplug the external hard drive's USB cable from the laptop as soon as I restart or switch it off, and once I am on the Ubuntu desktop I plug the USB cable and use the external hard drive normally

I hope that was helpful:neutral:

i apologize if i haven't been clear enough......i hav installed ubuntu to my external hdd - properly, taken care that the MBR is written to /dev/sdb (well, sd**b** in my case). then when i boot off of it, i cum to grub prompt and it doesn't go any further. But i take my hdd to my friend's house, plug it into his computer, boot off of it and i hav no such issues - ubuntu boots, runs smoothly. But this wont happen with my pc, even though my pc is better than his !

---

### Post by Fxy on 2011-01-02
If you can get as far as a prompt window for entering commands then try entering the following...

> startx

...That command usually starts the gui/desktop from within the prompt

---

### Post by ttakun on 2011-01-02
When you start your computer can not you see a GRUB menu listing the available Operating Systems?
Instead of that you get the grub prompt (grub>)?
Can you run the following command at grub prompt and paste the result?
**cat /boot/grub/grub.cfg**

---

### Post by starion on 2011-01-03
[SIZE=2][FONT=Verdana]Here is the problem........i did some research and finally now i know wat the problem is - [/FONT]
[/SIZE][SIZE=2]Using [FONT=Courier New]ubiquity [FONT=Verdana]I installed ubuntu 10.10 to my External HDD (WD Passport 400GB). I made sure that the bootloader is placed in sd**b**[/FONT][/FONT] (sd**b** in my case), and NOT in hd0. When I booted off of it, instead of getting into ubuntu, it loaded the grub prompt (**grub>**) [grub version = 1.98]. There, when i did [FONT=Courier New]ls (hd0,1)[/FONT] [FONT=Verdana]in which **hd0** is supposed to be my primary windows hard disk but unfortunately, grub sees it as my ubuntu hard disk. This is causing the confusion and the booting problem[/FONT]. The [FONT=Courier New]ls [FONT=Verdana]results in showing the contents of the boot partition which sd**b1**[/FONT][/FONT]. **SO, UBUNTU SHOWS MY EXTERNAL HDD AS sdb (which is hd1) AND GRUB READS IT AS hd0 (which apparently is sda)**. what do I do to fix it ?? However my friend's computer doesn't get confused as such and that is why it was booting properly into ubuntu....

[/SIZE]

---

