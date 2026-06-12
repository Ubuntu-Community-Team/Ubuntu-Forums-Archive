---
title: "formatting window's partition"
date: 2011-11-13
forum: General Help
---

### Post by citizenlame on 2011-11-13
Hi all. I run Window's 7 and Ubuntu on my Dell and I've decided that my Window's partition is so far gone that the best option is to format it and start fresh. Does anyone have experience in this? I'm wondering how, if it all, this will affect my Ubuntu partition.

---

### Post by Miljet on 2011-11-13
If you are talking about reinstalling Windows, yes it will affect Ubuntu. The Windows installation will replace Grub in the Master Boot Record of your hard drive and you will only be able to boot into Windows.

This is easily repairable using a Live CD. There are literally hundreds of guides on how to do that. Here is a link to one such guide.
[http://linuxpoison.blogspot.com/2011/06/how-to-reinstall-grub-2-in-ubuntu-using.html](http://linuxpoison.blogspot.com/2011/06/how-to-reinstall-grub-2-in-ubuntu-using.html)

---

### Post by Mark Phelps on 2011-11-14
Presuming that Ubuntu is in a separate partition, do not use Linux utilities to reformat the Win7 OS partition. Instead, simply remove the Win7 OS partition and leave the unallocated space alone.

Then, when you boot from the Wn7 DVD, choose the unallocated space and let the Windows installer do the formatting. It tends to work out better that way.

---

