---
title: "reduce available memory in ubuntu 9.10"
date: 2010-04-29
forum: General Help
---

### Post by acosgaya on 2010-04-29
Hi,

I want to set a limit on the available RAM in my Linux machine, it currently has 4GB of RAM, and in order to perform some experiments I need the system to recognize and use only 1GB. I don't want to limit the amount of memory to one particular process (like with ulimit), but to the whole system. The OS in Ubuntu 9.10 . 
Somewhere a long time ago (for Fedora) I read about editing grub, so that at boot time the limit is set, it might be something along those lines, but not really sure.

I'd appreciate some help.

Thanks

-A

---

### Post by P4man on 2010-04-29
try adding 

mem=1024M

as kernel option. 

Got that from here:
[http://tldp.org/HOWTO/BootPrompt-HOWTO-3.html](http://tldp.org/HOWTO/BootPrompt-HOWTO-3.html)

If that doesnt work, the page explains how to set up a ram disk, so make a 3gb ram drive :)

---

### Post by The Thunder Chimp on 2010-04-29
Please make sure you have some swap memory, because lowering RAM can make the system crash if no swap is available.

---

### Post by bodhi.zazen on 2010-04-29
> **P4man said:**
> try adding 

mem=1024M

as kernel option. 

Got that from here:
[http://tldp.org/HOWTO/BootPrompt-HOWTO-3.html](http://tldp.org/HOWTO/BootPrompt-HOWTO-3.html)

If that doesnt work, the page explains how to set up a ram disk, so make a 3gb ram drive :)

Either that ^^ or install KVM / Virtualbox and play in a VM with 1 Gb RAM :p

---

### Post by acosgaya on 2010-04-29
I do have a 2GB of swap, so I have considered that.

doing the 

'mem='

to specify the amount of memory (to limit the amount of memory available to linux), is exactly what I want.

Now, how do I do that, what do I have to edit?

thanks

-A

---

### Post by P4man on 2010-04-29
you add it to the kernel options in grub. Since this is for an experiment, you dont want it permanent, follow these instructions:

[https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Temporarily%20For%20An%20Existing%20Installation](https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Temporarily%20For%20An%20Existing%20Installation)

rather than adding vga=whatever, add mem=1024M

---

### Post by acosgaya on 2010-04-29
> **P4man said:**
> you add it to the kernel options in grub. Since this is for an experiment, you dont want it permanent, follow these instructions:

[https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Temporarily%20For%20An%20Existing%20Installation](https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Temporarily%20For%20An%20Existing%20Installation)

rather than adding vga=whatever, add mem=1024M

I have Ubuntu 9.10, the instructions there do not seem to apply anymore, and the link it points to for Grub2, doesn't say how to do it :(

any ideas?

---

### Post by P4man on 2010-04-29
> **acosgaya said:**
> I have Ubuntu 9.10, the instructions there do not seem to apply anymore, and the link it points to for Grub2, doesn't say how to do it :(

any ideas?

its really the same for grub2. Are you getting grubs menu? If so, press E, find the kernel line, press E again and add the parameter. Then I think control+X to boot (it says so at the bottom).

You can also add it in /boot/grub/grub.cfg
That will be overwritten next update, but thats okay here.

---

### Post by acosgaya on 2010-04-29
> **P4man said:**
> its really the same for grub2. Are you getting grubs menu? If so, press E, find the kernel line, press E again and add the parameter. Then I think control+X to boot (it says so at the bottom).

You can also add it in /boot/grub/grub.cfg
That will be overwritten next update, but thats okay here.

I followed the instructions on the GRUB menu, added 'mem=1024M' and it didn't work, I still see my 4gb when doing 'top' or 'free -m'

As for editing grub.cfg, it says it will be overwritten on restart as it is automatically generated, and I should change it.

any idea?


-A

---

### Post by P4man on 2010-04-29
Lets verify if you did it right. can you post the output of 

```
cat /proc/cmdline
```

And yeah you can put it in grub.cfg if you know where to put it. It will indeed to be overwritten next time you update grub or installl new kernel, but thats not a problem in your case. but if you did it right, putting it in grub.cfg wont help.

---

### Post by P4man on 2010-04-29
edit: nvm, im wrong, its not case sensitive

---

### Post by acosgaya on 2010-04-29
> **P4man said:**
> Lets verify if you did it right. can you post the output of 

```
cat /proc/cmdline
```

And yeah you can put it in grub.cfg if you know where to put it. It will indeed to be overwritten next time you update grub or installl new kernel, but thats not a problem in your case. but if you did it right, putting it in grub.cfg wont help.

Here is the output

~$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-2.6.31-21-generic-pae root=UUID=d74598f6-b8ca-45d9-8e37-4b23dee3b6e8 ro quiet splash

---

### Post by P4man on 2010-04-29
then you did it wrong. The mem option is not showing and it should. I just tested and it works fine the mem switch.

Try again. Go to grub, press E to edit your entry, find the kernel line, I think it looks like this:

BOOT_IMAGE=/boot/vmlinuz-2.6.31-21-generic-pae root=UUID=d74598f6-b8ca-45d9-8e37-4b23dee3b6e8 ro quiet splash

Its across 2 rows probably.  (use the END key on your keyboard to jump to the end, from the previous line if its across 2 lines)

Just add the mem=1024m so it looks like:

BOOT_IMAGE=/boot/vmlinuz-2.6.31-21-generic-pae root=UUID=d74598f6-b8ca-45d9-8e37-4b23dee3b6e8 ro quiet splash **mem=1024m**



control+x to boot.

Works here.

**edit:** alternatively, do the same in grub.cfg, just make sure you edit the correct kernel line (the one you will boot)

---

### Post by P4man on 2010-04-29
Here is my machine castrated to 1500m
```

bob@bob-desktop:~$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-2.6.32-21-generic root=UUID=1c1098fb-2fc9-475f-ac1d-fdf921038360 ro quiet splash vga=792 **mem=1500m**

bob@bob-desktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          **1467**        864        603          0         44        319
-/+ buffers/cache:        499        967
Swap:            0          0          0
bob@bob-desktop:~$ 

```
(wouldnt set it less as I have no swap :) )

---

### Post by acosgaya on 2010-04-29
> **P4man said:**
> then you did it wrong. The mem option is not showing and it should. I just tested and it works fine the mem switch.

Try again. Go to grub, press E to edit your entry, find the kernel line, I think it looks like this:

BOOT_IMAGE=/boot/vmlinuz-2.6.31-21-generic-pae root=UUID=d74598f6-b8ca-45d9-8e37-4b23dee3b6e8 ro quiet splash

Its across 2 rows probably.  (use the END key on your keyboard to jump to the end, from the previous line if its across 2 lines)

Just add the mem=1024m so it looks like:

BOOT_IMAGE=/boot/vmlinuz-2.6.31-21-generic-pae root=UUID=d74598f6-b8ca-45d9-8e37-4b23dee3b6e8 ro quiet splash **mem=1024m**



control+x to boot.

Works here.

**edit:** alternatively, do the same in grub.cfg, just make sure you edit the correct kernel line (the one you will boot)

It works!

the problem was that i added the 'mem=' at the end of the wrong line.

Thanks a lot!

---

### Post by acosgaya on 2010-04-29
Hi,

now I want to add the mem=1024m permantly, so that I don't have to do this every time  I restart the machine (when I'm done with my experiment I'll go back to my original 4GB).

I did all the following, but I cannot see my menu entry on the grub list (btw, the grub menu is hard to catch, it goes to fast even with pressing ESC multiple timee)

I added the following lines to file  /etc/grub.d/40_custom

menuentry "Ubuntu, Linux 2.6.31-21-generic-pae-custom" {
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set d74598f6-b8ca-45d9-8e37-4b23dee3b6e8
	linux	/boot/vmlinuz-2.6.31-21-generic-pae root=UUID=d74598f6-b8ca-45d9-8e37-4b23dee3b6e8 ro   quiet splash mem=1228m
	initrd	/boot/initrd.img-2.6.31-21-generic-pae
}

I did upgrade-grub, but the new line it doesn't appear; it shows the following, but not my 'custom' one:

~$ sudo update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.31-21-generic-pae
Found kernel: /boot/vmlinuz-2.6.31-20-generic-pae
Found GRUB 2: /boot/grub/core.img
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

I also did ~$ sudo grub-mkconfig, it appears the, but again, doesn't show in the grub menu (nor in /boot/grub/grub.cfg)

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "Ubuntu, Linux 2.6.31-21-generic-pae-custom-adan" {
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set d74598f6-b8ca-45d9-8e37-4b23dee3b6e8
	linux	/boot/vmlinuz-2.6.31-21-generic-pae root=UUID=d74598f6-b8ca-45d9-8e37-4b23dee3b6e8 ro   quiet splash mem=1228m
	initrd	/boot/initrd.img-2.6.31-21-generic-pae
}
### END /etc/grub.d/40_custom ###


any ideas?

---

### Post by acosgaya on 2010-04-29
I had to edit directly the grub.cfg, and that worked. I didn't want to do it that way, but it works for now.

---

