---
title: "DESPERATE!! I can't edit my boot menu!"
date: 2006-06-26
forum: General Help
---

### Post by sbddude on 2006-06-26
I have tried the suggestions of those on here and I STILL can't figure out how to make windows boot by default or change the number of seconds it will wait. Any changes I make to menu.lst seems to mean nothing. The changes are not reflected on next boot. Please help!! I don't want to give up Ubuntu!

---

### Post by aysiu on 2006-06-26
Are you editing the /boot/grub/menu.lst file from the right partition? It's just Windows and Ubuntu, right?

You're not triple-booting with another Linux operating system?

Can you post the output of this command? ```
cat /boot/grub/menu.lst
```

---

### Post by scxtt on 2006-06-26
judging from your other thread, you just created a menu.list (and anything in the /boot/grub directory), which would be pointless ... seems to me that your grub install is somewhere you're not aware of (possibly since you stated this: "I am booting from sdb. sda is my work hard drive and cannot be touched.") ...

---

### Post by aysiu on 2006-06-26
If what scxtt is saying is true, then you should [install Grub to the MBR](http://ubuntuforums.org/showthread.php?t=24113).

---

### Post by sbddude on 2006-06-26
I'll try those suggestions. Can I do a grub install with a USB DVD-ROM drive?

---

