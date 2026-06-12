---
title: "Trash icon won't empty"
date: 2010-07-01
forum: General Help
---

### Post by irishgoth8822 on 2010-07-01
Hi all,

This is just one of those annoying but superficial things: When I empty my recycle bin, the items fully delete (as far as I can tell) but the icon for the trash remains a full trash can. Fixes?

I have 10.04

---

### Post by irishgoth8822 on 2010-07-01
Addendum:
I've been surfing root to see if there were any files in the root trash, but when I try to click on the trash folder it says "Files cannot be displayed"--so I'm pretty sure that's why my icon isn't emptying, but since I can't get the root trash to open, I can't clear it out. Any suggestions?

---

### Post by Vaphell on 2010-07-01
is there anything in the output of
```
ls -al ~/.local/share/Trash/files
```

---

### Post by irishgoth8822 on 2010-07-01
> ls -al ~/.local/share/Trash/files
total 8
drwx------ 2 meghan meghan 4096 2010-07-01 14:54 .
drwx------ 5 meghan meghan 4096 2010-04-26 18:10 ..

the above^

---

### Post by LMP900 on 2010-07-01
This can happen when you delete something from an external drive and eject the drive before emptying the trash. If you plug the drive back in and empty the trash, the icon should show empty. A reboot may also fix this.

---

### Post by irishgoth8822 on 2010-07-01
Thank you, that was exactly the problem. I forgot I used my flash drive shortly after upgrading to 10.04...

---

