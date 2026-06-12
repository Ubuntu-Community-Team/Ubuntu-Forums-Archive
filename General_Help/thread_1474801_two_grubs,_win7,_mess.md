---
title: "two grubs, win7, mess"
date: 2010-05-06
forum: General Help
---

### Post by skan on 2010-05-06
Hi

I've just installed Ubuntu 10.04

/dev/sda1 -> Windows 7 reserved
/dev/sda2 -> Windows 7
/dev/sda3 -> Linux ext4
/dev/sda4 -> swap

I'd like to boot using Windows 7 boot manager (I don't dare to put grub in the MBR).

I've used EasyBCD to add a new entry for Ubuntu.

[IMG]http://i44.tinypic.com/xbl9qs.jpg[/IMG]

Then I added Grub to /dev/sda3

And I get this:

[IMG]http://i39.tinypic.com/33u528h.jpg[/IMG]

The problem is that it always shows (hd0,0) instead of (hd0,2). I must change it every time I boot.
I've tried to install grub again but I always get the same.

And another problem.  After that Grub menu it deesn't load Linux but it loads a second grub menu

[IMG]http://i44.tinypic.com/2hqrr60.jpg[/IMG]
that loads Linux properly.

I guess I've installed two Grubs.

How can I remove the first Grub menu (Grub4dos) and make Windows 7 load the second (the good one)?
or how can I remove the second one and change (hd0,0) to (hd0,2) in the second?
or any other idea


regards

---

### Post by Mark Phelps on 2010-05-06
Please don't take this as an insult, but you should really be posting your EasyBCD questions on the correct forum -- the NeoSmart Techology forums.  They have an EasyBCD support section in their forums and they have tutorials available for doing what you want.

Not saying folks here can't help -- just saying the best source of info is the folks that develop the product you're using.

---

### Post by skan on 2010-05-06
The problem is not related with EasyBCD but with two installations (error) of Grub
I don't want to remove nor change what EasyBCD did.

OK, let imagine I've just posted the last two pictures, I didn't use EasyBCD, just Grub

---

