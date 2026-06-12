---
title: "group default.plymouth is broken"
date: 2011-05-25
forum: General Help
---

### Post by lucazade on 2011-05-25
If I try to change the theme I get this error and plymouth is displayed only in text mode:

$ sudo update-alternatives --config default.plymouth

update-alternatives: warning: forcing reinstallation of alternative /lib/plymouth/themes/ubuntu-logo/ubuntu-logo.plymouth because link group default.plymouth is broken.
update-alternatives: warning: not replacing /lib/plymouth/themes/default.plymouth with a link.

How to fix this?
I am using ubuntu 11.04

$ cat /proc/fb
0 VESA VGA

ls -l /etc/alternatives/default.plymouth
lrwxrwxrwx 1 root root 53 2011-04-27 08:32 /etc/alternatives/default.plymouth -> /lib/plymouth/themes/ubuntu-logo/ubuntu-logo.plymouth

[https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/788138](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/788138)

---

### Post by woodyg on 2011-08-07
Same here. What to do? :confused:

---

### Post by phillat5dock on 2011-12-29
I am very much a noob at Ubuntu and I had this problem myself.

This what I think has happened.
I was trying to fix/change the way the Plymouth splash screen looks.
In the processes I have edited /lib/plymouth/themes/default.plymouth (thinking I was doing something useful!!)

BUT default.plymouth is actually a link from /etc/alternatives/default.plymouth , and this is a link from /lib/plymouth/themes/<theme_of_your_choice>/<theme_of_your_choice>.plymouth

[In terminal type ls -l /etc/alternatives]

To fix this I had to remove the offending file

sudo rm /lib/plymouth/themes/default.plymouth

and then use ln to recreate the link

from memory ...

sudo ln /etc/alternatives/default.plymouth /lib/plymouth/themes/default.plymouth


It seems a very round about way of achieving something.

After correcting the links run

sudo update-alternatives --config default.plymouth

again. The error message should not appear this time.

Now, you will need to run one more command to update the boot images and you are done.

sudo update-initramfs -u

---

