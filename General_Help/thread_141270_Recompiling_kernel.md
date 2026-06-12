---
title: "Recompiling kernel"
date: 2006-03-07
forum: General Help
---

### Post by marcinpisz1 on 2006-03-07
Hi:confused: 

I just switched from mandriva 2006 to ubuntu, not sure if it was worht the switch though.  One thing that I knew how to do is to recompile the kernel , lilo added the kernel automatically.  Is there like a 5 step method summurized to recompile the kernel in ubuntu

in mandriva it went install source rpm
mrproper
edit name in makefile
copy defconf from /usr/src/linux/i386/arch to usr/src/linux
run make xconfig
{modified it to scsi no multi lun for my buggy scanner to work and otehr }
make bla && bla &&bla  && bla can't remeber the comands but have them in a file on a different ciomputer
then I run 
make blab && bla and rebooted the system with the new kernels on the list to select to boot from new kernel.  

does anyone knos how to do this in ubuntu?
I will add it to the documentation if I can.
Also recompling with gcc4 will let me install nvidia drivers easily

---

### Post by evilgold on 2006-03-08
I dont want to be mean or anything but, you should try searching the forums before you ask a question.

Anyways here:
[http://www.ubuntuforums.org/showthread.php?t=85064](http://www.ubuntuforums.org/showthread.php?t=85064)

kernel compilation is mostly the same on all distros as far as i know.

---

### Post by az on 2006-03-08
Look here about installing a pre-built binary driver for your nvidia card. You would have to rebuild those drivers, too, if you want to recompile your kernel.

[https://wiki.ubuntu.com/BinaryDriverHowto](https://wiki.ubuntu.com/BinaryDriverHowto)

Why do you need to recompile your kernel?

---

### Post by Harry_Sack on 2006-03-15
[QUOTE=azz]Look here about installing a pre-built binary driver for your nvidia card. You would have to rebuild those drivers, too, if you want to recompile your kernel.

[https://wiki.ubuntu.com/BinaryDriverHowto](https://wiki.ubuntu.com/BinaryDriverHowto)

Why do you need to recompile your kernel?[/QUOTE]


Why do you always say that?   ;) 
Maybe someone doesn't NEED to, they just WANT to.  :cool: 
Not sure this is the case here though.

[http://www.ubuntuforums.org/showthread.php?t=56835&highlight=update+grub](http://www.ubuntuforums.org/showthread.php?t=56835&highlight=update+grub)

[http://www.ubuntuforums.org/showthread.php?t=43065&highlight=ck+patch](http://www.ubuntuforums.org/showthread.php?t=43065&highlight=ck+patch)

---

