---
title: "Grub loads Grub and so on...."
date: 2006-03-22
forum: General Help
---

### Post by can_climber on 2006-03-22
edited to say: Linux boots fine. Windows does not boot.

Hello,

  I was having some trouble with grub that eneded up with me re-installing the grub package to hda1(a drive that acutally contains windows ME.). Linux is on the drive hdb1.  Anyway, I played with the menu.lst and put my windows entry right below the most recent linux entry for convience.  After the grub re-install all was good. but ....After I upgraed to the latest kernel release, the windows entry was gone!  I wrote one back in but things havent been working out.  When I select the option to boot windows, the commands in menu.lst are echoed to the screen and then the Grub just comes back up again?

I am sure this is an elementry prob, but I cant figure out what I did wrond in the menu.lst.  Windows ME is still there.... and it mounts just fine in linux.  Not sure why its not booting.

here is the important part of my menu.lst:
## ## End Default Options ##

title		Ubuntu, kernel 2.6.12-10-386 
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hdb1 ro single
initrd		/boot/initrd.img-2.6.12-10-386
boot

title		Ubuntu, kernel 2.6.12-9-386 
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hdb1 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin  
boot

title		Windows ME
rootnoverify	(hd0,0)
makeactive
chainloader	+1
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

I would really appreciate any help.  BTW, I am really enjoying ubuntu, and even though I cant access any windows programs (just the files), I must say, I dont miss anything.

-Caleb

---

