---
title: "Uninstalling Ubuntu - Dual Boot"
date: 2010-06-22
forum: General Help
---

### Post by Football2010 on 2010-06-22
Hi all,

I dual booted Ubuntu on Windows Vista 32bit. I used the method which involved burning the .ISO image onto a CD.

I can easily switch between each operating system by pressing F10 at the start of the boot and choosing which OS to use.

As I do not wish to use Ubuntu right now, this can get tedious as I would rather a boot from the start, back to Windows Vista.

Could anyone point me in the right direction or explain the method in regards to removing Ubuntu from the dual boot list and to get your PC back to its post-installation state?

Thanks in advance.

---

### Post by -humanaut- on 2010-06-22
Do you want to completely remove Ubuntu or just have grub default to Windows?

---

### Post by oldfred on 2010-06-22
Is not f10 just a single boot selection? What boots if you do not use f10?

If you only want Vista and you do not have the windows boot loader in the MBR, that is the first thing you need to do. Use your Vista repair CD and run the command fixMBR.

---

### Post by Football2010 on 2010-06-23
> **oldfred said:**
> Is not f10 just a single boot selection? What boots if you do not use f10?

If you only want Vista and you do not have the windows boot loader in the MBR, that is the first thing you need to do. Use your Vista repair CD and run the command fixMBR.

Ubuntu boots if I do not click F10.

So this will remove Ubuntu?

Also, I do not have a repair CD but I did download the Neo Tech one. Is this okay?

---

### Post by Football2010 on 2010-06-23
Solved.

I installed EasyBCD to reinstall my bootloader, then deleted the Ubuntu partition.

Didn't realise it was so easy to do.

Thanks for your help anyway!

---

