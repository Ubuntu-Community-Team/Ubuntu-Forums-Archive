---
title: "Editing grub for fedora partition"
date: 2009-08-27
forum: General Help
---

### Post by pwhipped on 2009-08-27
I installed ubuntu first. I then booted fedora 11 live. I partitioned a /boot at hd0,3 and installed the bootloader on that partition. I then put /root on hd0,4. I can't figure out how to edit grub to boot fedora now... From what I've read I thought it would be:

title Fedora
root (hd0,3)
kernel /boot/vmlinuz-2.6.29.4-167.fc11.i586 ro root=/LABEL=/ rhgb quiet
initrd /boot/initrd-2.6.29.4-167.fc11.i586.img
chainloader +1

This gives me a file not found error when I try to boot the OS in grub. :/ Any help would be greatly appreciated. Thanks ahead of time.

---

### Post by bchurchill on 2009-08-27
This is a common problem... I've struggled with it before.

One cool trick is from the grub menu press 'C'.  This drops you to a grub command line.  Then you can type the same commands ie

root (hd0,3)
kernel **(hd0,3)/**boot/vmlin...
initrd (hd0,3)/boot/...
chainloader +1

then you'll see where errors are when commands don't work.  As a plus, you can type Cntl-D for it to show you an autocomplete list e.g.

kernel (hd0,3)/boot/[Cntl-D] will list all the files available

You can also use tab to autocomplete.  Then carefully check your menu.lst file.  You can also look in /boot on fedora to check the kernel/initrd names.  I've misspelled things so many times in menu.lst, it's very common to make a tiny typo.

[https://help.ubuntu.com/community/GrubHowto#Manually%20boot%20into%20a%20Linux%20OS](https://help.ubuntu.com/community/GrubHowto#Manually%20boot%20into%20a%20Linux%20OS) has more info if necessary.

---

### Post by pwhipped on 2009-08-27
Does root reference where fedoras root is? Because /root is hd0,4. That's the only thing I could find wrong with it. Thanks for the reply, I will try using the autocomplete and error feature of grub. I didn't even know about those functions.

---

### Post by bchurchill on 2009-08-27
> **pwhipped said:**
> Does root reference where fedoras root is? Because /root is hd0,4. That's the only thing I could find wrong with it. Thanks for the reply, I will try using the autocomplete and error feature of grub. I didn't even know about those functions.

It's a little tricky.   Grub numbers partitions starting at 0, so for example, /dev/sda4 is actually (hd0,3).  

the root command in grub sets the partition the kernels are installed in.  You also need root= in the kernel line to specify to the kernel which partition is /.  These may actually be different.  For example if your /boot partition including the fedora kernel is /dev/sda2 is seperate from your fedora installation on /dev/sda3 you'd use something like

title...
root (hd0,1)             (remember this refers to the second partition)
kernel (hd0,1)/vmlinuz.... root=/dev/sda3
initrd (hd0,1)/initrd...
chainloader +1

The path you specify for the kernel is relative to the path of (hd0,1), so in this example the /boot partition doesn't contain a /boot folder, so that doesn't show up in the commands.

If instead your /boot containing fedora kernels is the same as your / then it would look more like the previous example.

I hope all this makes sense.  If you're still having trouble, tell us what partition everything is on or post the output of sudo fdisk -l.

---

### Post by adrianx on 2009-08-27
Fedora 11, in my case, has a separate /boot partition (/dev/sd**a5**). This is how I do it in Ubuntu's menu.lst:
```
title       Fedora 11
root        (hd**0**,**4**)
configfile  (hd**0**,**4**)/grub/grub.conf
```The nice thing about using  "configfile" is that you don't have to edit menu.lst when Fedora gets a kernel update.

Edit: If you don't have a separate boot partition, you should use something like "configfile (hd0,4)/boot/grub/grub.conf".

---

### Post by pwhipped on 2009-08-27
Thanks for the help guys. I got it working. :) Now that I've used it for a few hours, I think I'm going to delete it. Fedora is not that great. FreeBSD coming right up.

---

### Post by bchurchill on 2009-08-28
Out of curiosity, what did you end up doing?  Did you figure out GRUB?

---

