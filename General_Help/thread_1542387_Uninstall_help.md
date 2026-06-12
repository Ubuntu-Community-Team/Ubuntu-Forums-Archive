---
title: "Uninstall help"
date: 2010-07-30
forum: General Help
---

### Post by Tlehnhart on 2010-07-30
[SIZE=3]I am new to this as anyone can be.. I had a guy I work with install Ubuntu 4. something on my acer laptop. The laptop had a dual boot with windows xp sp3. After awhile I started to have boot issues.. it would say something about realtek  Etc etc. I would ctrl atl delete and then it would usually boot to the grub menu.  I read others had the same errors and had figured out it was ubuntu causing this issue.    I have decided I really want to remove ubuntu and I read several post on how to do this. 1 st issue most say to remove ubuntu partition then reboot with window xp disc. I do not have a xp boot disc, only a acer back up/restore. So anyway I moved forward and ventured into the windows manager to delete the partions, 2nd issue I was not sure what partions to delete, as they where not labeled Ubuntu or grub. There where 2 however that to seemed to be the partion of ubuntu. I deleted these and now when I try to boot it says "Grub loading stage 1.5, Grub loading please wait.... Error 22 "  I try to boot from my acer backup no go.... I got a home made xp boot disc and the same message appears every time !! Is there any one who may be able to steer me in the right direction on how to resolve this issue and return to just my xp machine????
[/SIZE]

---

### Post by dv3500ea on 2010-07-30
> **Tlehnhart said:**
> [SIZE=3]Ubuntu 4.[/SIZE]
Not sure what what version you are using. Ubuntu 4.10 is extremely old and no longer supported.

You may have more success by booting from the Ubuntu live CD and using the partition manager to delete the Ubuntu partition and increase the size of the Windows one to fill the whole disk. 

You will find the partition manager by going to System -> Administration -> Partition Manager (I think), or pressing Alt-F2 and entering ```
gparted
```

---

