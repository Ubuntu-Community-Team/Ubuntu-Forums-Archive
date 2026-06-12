---
title: "Deleted partition and now I cannot boot"
date: 2009-10-31
forum: General Help
---

### Post by fs_tigre on 2009-10-31
Hi,

Last night I decided to reinstall Ubuntu and while running Widows I made the most $tu&()& desition. I went and deleted the partition where Ubuntu was installed using partition magic ( I know I know it was $tu&%*) I thought it was going to delete the entire partition as well as the OS (Ubuntu) and then I was going to be able to re-install it later but to my surprise I cannot even access the partition where Windows is install at all. When I turn on my computer all I see is a black screen with some text that says;


> GNU GRUB version 0.95 (640K lower / 392128K upper memory)

Minimal BASH-like line editing is supported. For the first word...

grub> _


And as you can imagine I don't know what to do and I don't want to loose some information in the windows partition.

Any idea how can I boot windows and start with a fresh Ubuntu install?

Is there a way to by-pass this screen?

I know I know, but I don't know what I'm doing

Thanks a lot

---

### Post by Turtle.net on 2009-10-31
I don't know exactly what you did with partitionmagic ... and I guess we will not talk about that ;)
Anyway, you should try to boot from a Ubuntu LiveCD and go through the install process.

---

### Post by phillw on 2009-10-31
> **fs_tigre said:**
> Hi,

Last night I decided to reinstall Ubuntu and while running Widows I made the most $tu&()& desition. I went and deleted the partition where Ubuntu was installed using partition magic ( I know I know it was $tu&%*) I thought it was going to delete the entire partition as well as the OS (Ubuntu) and then I was going to be able to re-install it later but to my surprise I cannot even access the partition where Windows is install at all. When I turn on my computer all I see is a black screen with some text that says;




And as you can imagine I don't know what to do and I don't want to loose some information in the windows partition.

Any idea how can I boot windows and start with a fresh Ubuntu install?

Is there a way to by-pass this screen?

I know I know, but I don't know what I'm doing

Thanks a lot

[http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm](http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm)

will help you work out what you want to do, it has info rebuilding your boot sector, next time - follow those instructions !! ;)

Phill.

---

### Post by mechro on 2009-10-31
Either reinstall Ubuntu which should restore your (Grub) boot options for Ubuntu and Windows.

Or reinstall the Windows boot loader using a Windows CD.

---

### Post by fs_tigre on 2009-10-31
> reinstall the Windows boot loader using a Windows CD


How can I do this, I don't see any options in the install CD other then repair and fresh reinstall.

---

### Post by fs_tigre on 2009-10-31
Problem solved - Re-installed Ubuntu.

Thanks a lot!

---

### Post by mechro on 2009-10-31
I'll take a guess that it's XP, so...

[http://www.ehow.com/how_5087994_fix-windows-xp-bootloader.html](http://www.ehow.com/how_5087994_fix-windows-xp-bootloader.html)

---

### Post by Turtle.net on 2009-10-31
Great choice !
:)

---

### Post by fs_tigre on 2009-11-01
Thank you all!

---

