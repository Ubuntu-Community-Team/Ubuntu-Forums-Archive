---
title: "dual boot ubuntu freebsd/openbsd"
date: 2011-01-17
forum: General Help
---

### Post by user sam on 2011-01-17
I'm having trouble configuring grub2 to boot freebsd. I know how to do it in grub, but grub2 is giving me grief. A little help?

---

### Post by highspider on 2011-01-17
--------------------------------------
sudo nano /boot/grub/grub.cfg
-----------------------------------------

menuentry "FreeBSD 8.1" {
    set root=(hd0,2,a)
    chainloader +1
}

- or -

menuentry "FreeBSD 8.1" {
set root='(hd0,2)'
chainloader +1
}
------------------------------------------

in grub.cfg it should say something like 

menuentry 'Ubuntu, linux 2.6....'{
   recordfail
   insmod ext2
   set root='(hd0,1)'
  ........
  ..........
}
ADD NEW BSD OPTION HERE


where it says (hd0,1) of the ubuntu boot   means ubuntu is installed on harddrive0, partition1
NOTE hard drives start from zero and partition start from one
edit the above FREEbsd with the correct hard drive and partition that it is installed on.
 
  
see also [http://forums.freebsd.org/showthread.php?t=5918](http://forums.freebsd.org/showthread.php?t=5918)

---

### Post by drs305 on 2011-01-17
I don't use either of those OS's but have seen those menuentries posted on these forums.

One thing to note is that if you place them in /boot/grub/grub.cfg they will be removed whenever update-grub is run - either by you or when the system updates.

A more permanent fix would be to add the entry to /etc/grub.d/40_custom, below the existing lines. This will add the menuentries at the bottom of your existing ones and will not be removed when update-grub is run.

If you would prefer to place them elsewhere in the menu, change the filename - 06_custom would be the first section of the menu, 11_custom would follow the linux entries.

Just make sure /etc/grub.d/40_custom is executable and run "sudo update-grub" to add the entries to the grub menu file (/boot/grub/grub.cfg).

---

### Post by user sam on 2011-01-22
I found a tutorial here: [http://lists.freebsd.org/pipermail/freebsd-doc/2009-November/016465.html]("http://lists.freebsd.org/pipermail/freebsd-doc/2009-November/016465.html")
works pretty well. thank you for answering. :KS

---

