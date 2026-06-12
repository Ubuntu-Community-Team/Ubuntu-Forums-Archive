---
title: "edit grub2 menu"
date: 2009-10-29
forum: General Help
---

### Post by sandyd on 2009-10-29
How do i edit the Grub2 Menu? (just wanna make it look nicer and clean up the long list of kernels)

P.S. like the fact that it actually detects my hidden DELL recovery partition, where grub1 would not. :)

---

### Post by Wiebelhaus on 2009-10-29
*Paying Attention* I'd like to know as well!

---

### Post by mcduck on 2009-10-29
You can simply use Synaptic Package Manager (or the Computer Janitor) to uninstall old kernels, and they will be automatically removed from the Grub menu. :)

Apart from that, Grub2 is configured in /etc/default/grub and the menu entries are created using configuration files located in /etc/grub.d/.

---

### Post by sandyd on 2009-10-29
> **mcduck said:**
> You can simply use Synaptic Package Manager (or the Computer Janitor) to uninstall old kernels, and they will be automatically removed from the Grub menu. :)

Apart from that, Grub2 is configured in /etc/default/grub and the menu entries are created using configuration files located in /etc/grub.d/.
i looked at /etc/grub.d/ and already had  a headache.

removing the kernels never looked easier.....](*,)

---

### Post by Wiebelhaus on 2009-10-29
> **carlee said:**
> i looked at /etc/grub.d/ and already had  a headache.

removing the kernels never looked easier.....

True , Same here. I like the old .lst. But I'm an old schooler and it looks like my way of doing things are being replaced more and more with every release.

Debian never looked more appealing.

---

### Post by hal8000 on 2009-10-29
Hi Carlee,  grub 2 have a look here:

[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

To save a little time the main config file is now
/boot/grub/grub.cfg (however it is not meant to be edited) which replaces the
old menu.lst

There is however a file that can be edited which is
/etc/default/grub

These changes are passed to grub.cfg when you run

sudo  update-grub

Hope that helps.

---

### Post by halhopism on 2009-10-29
Looks like such a gem of a spot mate! I love the look of those big old trees running along the banks.
Great to see the bass are still in there growing big and fat!

---

### Post by vahnx on 2009-10-29
> **hal8000 said:**
> 

There is however a file that can be edited which is
/etc/default/grub

These changes are passed to grub.cfg when you run

sudo  update-grub

Hope that helps.

It doesn't list the entries though. I ran commands to remove the recovery and memtest but now I would like to re-arrange the list order.

---

### Post by benner on 2009-11-07
Same here!  I need to rearrange the boot sequence.

---

### Post by yochaigal on 2009-11-07
This should help:

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

You basically should never edit /boot/grub/grub.cfg
It gets rewritten each time you run update-grub2
You need to edit /etc/grub.d/40_custom  (copy the menu entries from grub.cfg, then rearrange them here).
You then need to take the executable property away from three files in /etc/grub.d/ 

sudo chmod -x /etc/grub.d/10_linux /etc/grub.d/20_memtest86+ /etc/grub.d/30_os-prober

Then do 

sudo update-grub2

And you should be good....

---

### Post by pearldrums on 2009-11-17
I tried moving my OS options around this way and it worked fine. However, I'd like to group them together with headers like this: 

MAIN OS OPTIONS:
Ubuntu
Microsoft windows XP
RECOVERY OPTIONS:
Ubuntu - linux ??.??.??.?? (recovery)
Ubuntu - linux ??.??.??.??
Ubuntu - linux ??.??.??.?? (recovery)
MEMTEST OPTIONS:
Memtest ??.??.??
Memtest ??.??.??

I don't know what the actual values are for the question marks, but do you get the idea? I've tried doing just a
menuentry "name"
or 
menuentry "name" {}
and neither of those work.

---

### Post by ranch hand on 2009-11-17
Read the link in my sig.  It is a simple intro with the very basics of grub2.

The first three link in it are the very best in depth info on grub2.

If you use the symbolic menu entry for your Ubuntu in a custom menu it will never need editing.

---

### Post by blegs38552 on 2009-12-05
I am not one to usually complain about Ubuntu (or Linux) being harder to work with than Windows, but the grub2 menu is a nightmare to edit. I just ran Synaptic Package Update which updated my Linux kernels. I now have two entries for all Linux options on my menu - tried rebooting, but it did not help. This is like The Fringe TV show - there are more than one of everything. Isn't there any easy way to edit this mess - grub 1 was much easier, and even the Windows start menus have apps to simplify the process. HELP!!!

---

### Post by ranch hand on 2009-12-05
If you read the link in my sig, there is a link to go back to grub-legacy in the links at the bottom.

---

### Post by blegs38552 on 2009-12-05
I ran sudo update-grub and the following was displayed in Terminal:

neil@ubuntu:~$ sudo udate - grub
[sudo] password for neil: 
sudo: udate: command not found
neil@ubuntu:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done
neil@ubuntu:~$ 

As can be seen, I now have two kernel entries, 2.31.14 and 2.31.16, both of which generate menu entries for generic, recover, and memtest. Windows 7 is now my 7th entry. Worse, if I leave grub to boot for itself without selecting a choice, it starts running memtest.

Sorry, but grub2 sucks, as far as I am concerned. I have yet to see a simple explanation telling me how I can make Windows 7 the top entry on the menu, and now, how I can get rid of the duplicate entries which, P assume, are the 2.31.14 entries.

These are the things that will prevent Linux from ever being considered a "ready for prime time" operating system.

---

### Post by tagra123 on 2010-05-02
> **yochaigal said:**
> This should help:

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

You basically should never edit /boot/grub/grub.cfg
It gets rewritten each time you run update-grub2
You need to edit /etc/grub.d/40_custom  (copy the menu entries from grub.cfg, then rearrange them here).
You then need to take the executable property away from three files in /etc/grub.d/ 

sudo chmod -x /etc/grub.d/10_linux /etc/grub.d/20_memtest86+ /etc/grub.d/30_os-prober

Then do 

sudo update-grub2

And you should be good....


This method is easy to do, easy to reverse, easy to understand, and works as expected. It gives the user  more control instead of some grub script, just like the menu.lst did.  Good Work!

---

### Post by DarthBrady on 2010-05-14
> **yochaigal said:**
> This should help:

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

You basically should never edit /boot/grub/grub.cfg
It gets rewritten each time you run update-grub2
You need to edit /etc/grub.d/40_custom  (copy the menu entries from grub.cfg, then rearrange them here).
You then need to take the executable property away from three files in /etc/grub.d/ 

sudo chmod -x /etc/grub.d/10_linux /etc/grub.d/20_memtest86+ /etc/grub.d/30_os-prober

Then do 

sudo update-grub2

And you should be good....

Thank You Very Much! Seemed tricky compared to editing menu.lst in the old GRUB, but once I gave it a try it worked perfect on the first try. You can even rename the entries after copying them. Now I finally have a nice, clean GRUB menu.

Screenshot:
[IMG]http://img194.imageshack.us/img194/4230/img0170kt.jpg[/IMG]

---

### Post by Gonzalo_VC on 2010-06-12
> **DarthBrady said:**
> ...Seemed tricky compared to editing menu.lst in the old GRUB, but once I gave it a try it worked perfect on the first try. You can even rename the entries after copying them. Now I finally have a nice, clean GRUB menu.

[COLOR="Navy"]Lucky you!
But I still think there should be an elegant way to edit and arrange the menu list... for after 2 or 3 upgrades in the kernel, you'll end up with a full page of boot options. 
I, at least, do not need/want this! And I like to edit some options and put something like "ugly window$" in my list also :popcorn:[/COLOR]

---

