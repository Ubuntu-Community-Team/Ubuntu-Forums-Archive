---
title: "Need help with GRUB"
date: 2012-08-03
forum: General Help
---

### Post by reagen on 2012-08-03
Hello, people. I just made a mistake I'm really hoping there's an easy way to fix it.

So I just started dual-booting.
In an attempt to make the GRUB boot menu dissapear and just boot Ubuntu everytime (Since now I got 2 boot screen everytime I turn on the machine. 1 from Windows, and then after I choose Ubuntu, the GRUB) I used the Grub Costumizer and uncheck all boxes. Now GRUB still appears, and but there's no choice at all and I can't boot Ubuntu.

So does anybody know how I can fix this? Any answer would be most appreciated. 
Thank You anyway.

---

### Post by oldfred on 2012-08-03
I do not know wubi.

Someone posted this when grub has problems. Your system should be configured ok, so you should be able to manually type in the commands to boot from the grub menu. When grub menu comes up hit e to get to grub command line. Not sure if commands should be a bit different when it is otherwise correct. Someone that knows wubi may know exact commands.
wubi:
Type this at "grub sh>" prompt:
ls
# what does it show at ls command? That may change what you type here:
set path=/ubuntu/disks/root.disk
linux /vmlinuz root=/dev/sda1 loop=$path ro
initrd /initrd.img
boot
#You might have to replace /dev/sda1 by /dev/sda2, or some other value. It has to be the partition containing Wubi. You can use
search -f $path

---

### Post by reagen on 2012-08-03
EDIT: That did it. I booted the live cd, install and run GRUB Costumizer. Choose the partition where my /boot is. And the settings show itself. And that's it! Just have to check everything again.

---------------------------------------------------------------------
Thanks for the quick reply, oldfred.

Unfortunately, I am not using Wubi.
I have an all Windows7 machine, shrink it's partition. And used the free space for Ubuntu 12.04. The install went right, and everything works great. It's just that there's 2 boot menu that I have to put command in everytime. 

First, the Windows one. Which I apply through some 3rd party software. That let me choose between Windows and Ubuntu. If I choose Windows, it boots as usual.
If I choose Ubuntu, however...

GRUB appears. Again letting me choose between Ubuntu, Windows, Memory Test, etc. 
Again, everything works great. It's just that I feel annoyed have to choose Ubuntu 2 times everytime. Thus, the googling-installing-applying of Grub Costumizer.

And then, due to my lack of understanding, it happens.

I got this idea of using Ubuntu LiveCD to use Grub Costumizer. See if I can return Grub settings to normal from there.
Will see and post result.

In the mean time, anymore suggestions/solutions?

---

