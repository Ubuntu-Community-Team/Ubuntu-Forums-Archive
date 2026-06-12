---
title: "Grub ISO9660 Project snag."
date: 2010-04-02
forum: General Help
---

### Post by Wiebelhaus on 2010-04-02
What was meant to be an hour long project has turned into something I'm banging my head against and that I need help with.

The Grub boot-able Multi-iso disc structure looks like this:

[IMG]http://lh5.ggpht.com/_fV49O9FSzXI/S7ahKxu_UUI/AAAAAAAABlQ/8obNJ4oPlPc/s720/minfilestruct.png[/IMG]

Now basically what I've done is loop-mount each iso and then cp the contents to the proper folder and then configure menu.lst to mount the contents of each folder and then create the grub iso with the this [GNU how to]("http://www.gnu.org/software/grub/manual/html_node/Making-a-GRUB-bootable-CD-ROM.html").

Here's what Grub's Menu.lst looks like (Note the bottom entry)

[IMG]http://lh5.ggpht.com/_fV49O9FSzXI/S7ahKlLk1ZI/AAAAAAAABlM/VoLkSbrRvw0/s576/menulst.png[/IMG]

*Left UBCD entry blank , didn't see any point in leaving the wrong info there*

Now the issue is all iso's mount perfectly except [UBCD5]("http://www.ultimatebootcd.com/") , This is a very important additive to this multi-disk , here's what UBCD's Structure looks like:

[IMG]http://lh5.ggpht.com/_fV49O9FSzXI/S7ahK1m7crI/AAAAAAAABlU/FMutt9ruoFQ/s576/ubcdexpand.png[/IMG]

I just cannot figure it out , I've tried mounting just the UBCD's .iso but I don't think Grub 1 can understand it and I cannot for the life of me figure out how UBCD boots , I've been scouring the Internet and cannot find much info at all. Now there's a lot of info on doing it on a jump drive but I'd like to do a CD for tech use in our shop , This is for internal use only unless someone just wants it then your more then welcome to it.

Here's the [Public link]("http://dl.dropbox.com/u/1014089/iso.tar.gz") to down load the exact structure I'm working on if you want to give it a shot or try to help out.

Here's the Code of Menu.lst:

#Testing grub menu


```


title AVG_LIVE_LINUX_DISC
kernel /AVG/isolinux/vmlinuz 
initrd /AVG/isolinux/initrd.lzm 

title HIRENS_BOOT_CD 
kernel /HIRENS/HBCD/memdisk
initrd /HIRENS/HBCD/boot.gz

title MINI_UBUNTU_NET_OR_COMMAND_LINE_INSTALL 
kernel /MINIBUNTU/linux 
initrd /MINIBUNTU/initrd.gz 

title PUPPY_LINUX.4.3.1
kernel /PUPP_LINUX.4.3.1/vmlinuz
initrd /PUPP_LINUX.4.3.1/initrd.gz 

title ULTIMATE_BOOT_CD.5.0
kernel 
initrd





```

As the [GNU manual]("http://www.gnu.org/software/grub/manual/html_node/Making-a-GRUB-bootable-CD-ROM.html") points out after you have compiled the disc the way you want it you create the iso with this command:

```
$ mkisofs -R -b boot/grub/stage2_eltorito -no-emul-boot \
         -boot-load-size 4 -boot-info-table -o grub.iso iso
```

Cheers and thanks for any help.

---

### Post by Wiebelhaus on 2010-04-02
pltmnky over at IRC #tlf (Texas Linux Fest) suggests taking a look at archlinux's new disks and see about taking advantage of chainloader.

Something like:

> # chainloaded grub 
rootnoverify (hd0,2) 
chainloader +1

---

### Post by Wiebelhaus on 2010-04-03
I can't figure out where to chainload to in the UBCD5 structure.

---

