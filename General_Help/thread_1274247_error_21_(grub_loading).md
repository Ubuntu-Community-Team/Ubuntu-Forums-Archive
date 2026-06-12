---
title: "error 21 (grub loading)"
date: 2009-09-24
forum: General Help
---

### Post by mimoza on 2009-09-24
today when I was starting up my comp (for the 1st time today), I've got
 
"GRUB loading stage1.5.

GRUB loading, please wait...
Error 21"

I've installed ubuntu on it a more than a month ago and it was working perfectly, until now.

I haven't been working anything in "/boot/" area. Ever.

Only thing which I have done is that I have installed xubuntu on my memory stick yesterday night. After that I restarted my comp and been working on it (in ubuntu, my username, my files, programs, all of the stuff - worked good as always). And while working in it, I removed mem. stick. And all worked fine. Nothing happened. And then I saved my settings and shut my comp off.

And now I am searching for a solution on my other pc.

Please, help me. Thanks in advantage.

---

### Post by ajgreeny on 2009-09-24
When you installed xubuntu on the memory stick, grub from that was probably installed on the mbr.  Now when you try to boot grub looks for the memory stick for all the grub files, can't find it and the error message appears.  Put the memory stick back in and you may get the machine to boot again to ubuntu.  If it works, from ubuntu use the command in terminal ```
sudo grub-install /dev/sda
```assuming your mbr is on the mbr on sda.  If it's on another disk, change the sda appropriately.

You can also use the live CD, xubuntu or ubuntu to restore grub from the hard disk
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by mimoza on 2009-09-24
thanks so much. :)

---

