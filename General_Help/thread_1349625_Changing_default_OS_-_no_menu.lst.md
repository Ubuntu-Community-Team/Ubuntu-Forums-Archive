---
title: "Changing default OS - no menu.lst"
date: 2009-12-08
forum: General Help
---

### Post by Aduntu on 2009-12-08
Hello,

I've installed 9.10 to a machine currently running Vista.  I don't mind using grub, but I'd like it to default to Windows now, instead of Ubuntu.  I've tried to adjust the menu.lst file, but there is not one.  

I used "sudo gedit /etc/default/grub" to locate this file:

[IMG]http://i378.photobucket.com/albums/oo225/justformyrandompictures/grub.png[/IMG]

I'm trying to figure out how to edit this so that grub defaults to Windows.

I read that I should edit "GRUB_DEFAULT=0" to read "GRUB_DEFAULT=4" but this only changes the default to a different version of Ubuntu.

Windows is the 7th item on my grub list

Any advice on how to set this to default to Windows?

This is my first time seeking advice on Ubuntu, so thanks in advance.

---

### Post by heyho on 2009-12-08
menu.lst is no more.

Search for grub2 configuration.

---

### Post by rahilm on 2009-12-08
that's because 9.10 doesn't have grub, now known as grub legacy.
It has grub2 which is very different from grub. If you want to know more try reading this:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by fouserge on 2009-12-08
If it's the seventh on the list then you just change that number to a 6.

The list is zero based therefore the first item on the list is 0 and the last item on the list is the number of items - 1. So if there are 7 items, to get the last item to be the default, you would put 6 as the default.

---

### Post by Marlonsm on 2009-12-08
Grub has changed in 9.10.
The menu.lst now has split in two files, /etc/default/grub and /boot/grub/grub.cfg

The second one is the important one, but it's always updating, so you shouldn't edit it manually. What you should do is to change the first one, because Grub uses it as a base for the other file.

You should look at the grub.cfg to see where Windows is in the list and change the number in the /etc/default/grub file using "sudo gedit".


Take a look here for more info:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by Aduntu on 2009-12-08
I am blown away by the incredibly fast responses.  I've never seen anything like it.

Thank you so much, adjusting the default to 6 made perfect sense, and solved my issue.

I've just begun my journey with linux, and I will be reading the information you've provided.

Thanks again.

---

