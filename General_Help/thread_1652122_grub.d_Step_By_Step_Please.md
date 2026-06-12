---
title: "grub.d Step By Step Please"
date: 2010-12-24
forum: General Help
---

### Post by fidgaf on 2010-12-24
I have Ubuntu 10.04 LTS installed and have discovered that menu.lst has gone with grub2 and I now have to do something incomprehensible in grub.d

I have dual boot with XP and I want to put Windows XP as the default and first boot option (not the last as it is now).

Could someone be so kind as to show me a complete idiot's step-by-step guide of how to move XP to the first in the list.






Bit o' history:

Sorry, but I can't paste any output to this forum.

Ubuntu will not connect to the Internet. It always did before Lucid Lynx but not now - See: [http://ubuntuforums.org/showthread.php?p=10275172#post10275172](http://ubuntuforums.org/showthread.php?p=10275172#post10275172)

My easy option is to remove Ubuntu altogether but having used it extensively since Hardy Heron (I think) I live in the faint hope that it will once again become a shining beacon of excellence it once was and not just a waste of space on my hard drive.

Maybe Santa will help. :o)

---

### Post by Quackers on 2010-12-24
As explained in the guide below, what you need to edit is /etc/grub/default not grub.d 
with the terminal command ```
gksu gedit /etc/default/grub
```

and the line you need to edit is this one
GRUB_DEFAULT=0
which will be the first proper line.
If you only have 2 entries in your grub menu Ubuntu will be 0 and XP will be 1 so you would change the line above to
GRUB_DEFAULT=1
Then you should save the file then quit the file and then in a terminal run
```
sudo update-grub
```

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by fidgaf on 2010-12-24
> **Quackers said:**
> As explained in the guide below, what you need to edit is /etc/grub/default not grub.d 
with the terminal command ```
gksu gedit /etc/default/grub
```

and the line you need to edit is this one
GRUB_DEFAULT=0
which will be the first proper line.
If you only have 2 entries in your grub menu Ubuntu will be 0 and XP will be 1 so you would change the line above to
GRUB_DEFAULT=1
Then you should save the file then quit the file and then in a terminal run
```
sudo update-grub
```

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

A bit of experimenting and I got it to default to XP using "4".

That's much better, thank you.

XP is still last in the list but I suppose that doesn't matter.

Thanks.

---

### Post by Quackers on 2010-12-24
Ah, you have other menu entries as well. If you want to get rid of some you can use that same guide :-)
The position of XP is not relevant, as long as it's now the default one.

---

