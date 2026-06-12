---
title: "lost &quot;kernel 2.6.28-13&quot; in boot options"
date: 2009-07-11
forum: General Help
---

### Post by Bezi on 2009-07-11
I used "Restore Original Settings" in "Start up Manger",
and it removed 2.6.28-13 version of kernel as an option to boot up, 
and only

Ubuntu 9.04, kernel 2.6.28-11-generic

is available as boot option, though before I also had the kernel 2.6.28-13 version as an option.

Plz tell me how can I fix it

I have used "sudo update-grub " many times, and although it says:

"Found kernel: /boot/vmlinuz-2.6.28-13-generic"

it does not fix /boot/grub/menu.lst

---

### Post by Finalfantasykid on 2009-07-11
You could always manually edit your grub menu.  I have done that several times to get rid of older kernel versions from showing up.  Just copy/paste what is already there for one of the kernels, and replace 11 with 13 and it should work.

title        Ubuntu 9.04, kernel 2.6.28-13-generic
uuid        8b7d86eb-2b03-4830-aef0-d3e3ae360d38
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=8b7d86eb-2b03-4830-aef0-d3e3ae360d38 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid        8b7d86eb-2b03-4830-aef0-d3e3ae360d38
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=8b7d86eb-2b03-4830-aef0-d3e3ae360d38 ro  single
initrd        /boot/initrd.img-2.6.28-13-generic

it will look something like this, but with different a different uuid of course.  Before manking any changes though, I would make a backup of your menu.lst, and also it might be a good idea to keep around the .11 version just until you are able to boot into .13, just incase something did not work.

---

