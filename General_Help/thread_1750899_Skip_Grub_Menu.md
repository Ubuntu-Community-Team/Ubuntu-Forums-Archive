---
title: "Skip Grub Menu"
date: 2011-05-06
forum: General Help
---

### Post by jim_deadlock on 2011-05-06
Can someone tell me how to skip the grub menu in Natty? The way I used to do it in /etc/default/grub no longer works.

---

### Post by luckyu on 2011-05-06
Just wondering do you have more then one operating system installed ?? 
Otherwise if it is just Ubuntu it should just boot straight in.

---

### Post by jim_deadlock on 2011-05-06
No just Ubuntu, I've always had the grub menu where you can choose which kernel to boot, but before in Maverick I used to be able to change the timeout settings or remove the grub menu altogether via the settings in /etc/default/grub but that file isn't there any more in Natty.

---

### Post by luckyu on 2011-05-06
Okay that is unusual because I am on Natty and there is such a file ...```
/etc/default/grub
``` 

Output the contents of these two directories for me
```
/boot/grub/
/etc/grub.d/

```

---

