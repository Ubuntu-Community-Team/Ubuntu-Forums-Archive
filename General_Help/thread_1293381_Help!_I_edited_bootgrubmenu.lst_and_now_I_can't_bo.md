---
title: "Help! I edited /boot/grub/menu.lst and now I can't boot!"
date: 2009-10-17
forum: General Help
---

### Post by sejomagno on 2009-10-17
Hi!

I was trying to change the resolution of the tty consoles, so I followed this post [http://ubuntuforums.org/showthread.php?t=215566]("http://ubuntuforums.org/showthread.php?t=215566") and edited /boot/grub/menu.lst
I added the following line:
# defoptions=vga=795 resume=/hda5
and added a "#" before the line that looked like the one before.

Several times I tried to update-grub, and a message asking about changes appeared. I selected the default option, "use the local file" or something like that. Because nothing happened when I went to the console with ctrl+alt+f1, I rebooted.

Now what I get is a grub menu with some kernel versions... the problem is that I cannot press "enter" to boot, and I don't know what I have to do in the grub console to fix it...

Any ideas? :confused:

Please help! 
Thanks!

---

### Post by sejomagno on 2009-10-17
:(
I could boot by using in grub:
kernel /vmlinuz root=/dev/sda1 ro vga=ask
boot

however, because rebooting I had the same problem, I did again update-grub, but choosing the first option, "use the package mantainer's version" (or something like that)... I rebooted, and now I can't even load grub....

---

### Post by PrePenguin on 2009-10-17
Put in the Live CD and recover Grub this way...
 
 
**Here&#8217;s the quick and easy way to re-enable Grub.**
1) Boot off the LiveCD
2) Open a Terminal and type in the following commands, noting that the first command will put you into the grub &#8220;prompt&#8221;, and the next 3 commands will be executed there. Also note that hd0,0 implies the first hard drive and the first partition on that drive, which is where you probably installed grub to during installation. If not, then adjust accordingly.
[INDENT]sudo grub
> root (hd0,0)
> setup (hd0)
> exit
[/INDENT]

---

### Post by sejomagno on 2009-10-17
Thanks!

I did what you said and apparently worked in the terminal of the live cd, but when I start the computer, it still only shows "GRUB loading, please wait"...

Do I have to chroot into the HD and do something?

thank you!

---

### Post by sejomagno on 2009-10-20
I tried several ways of reinstalling GRUB that didn't work.
Finallly what I did was changing to LILO following [these instructions]("http://www.bauer-power.net/2007/08/changing-from-grub-to-lilo-ubuntu-704.html"). 

Maybe in the weekend I'll try to get back to GRUB :-P

---

