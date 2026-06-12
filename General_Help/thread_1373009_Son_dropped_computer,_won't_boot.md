---
title: "Son dropped computer, won't boot"
date: 2010-01-05
forum: General Help
---

### Post by campbuds on 2010-01-05
Sorry guys but this is the only place I know to go to get help.

My dual boot Vaio was dropped by my son yesterday while in ubuntu. Funny enough ubuntu is fine but now I cannot get Vista to boot or it's restore partition.

A surface scan revealed there are errors on the disk. The drop must have caused the heads to bounce off the disc and damage the windows partition.

While chkdsk was able to find surface errors, I cannot get scandisk to run. It says "could not lock drive c"

I am using the utilities that came with the Vaio restore disks.

Is there a tool maybe in ubuntu I can run that could possibly fix my problem? Scandisk always used to do a pretty decent job for me.

Any other solutions are welcomed as well. I would prefer not to have to start from scratch, that takes so long with windows.

---

### Post by mart78 on 2010-01-05
I wouldn't know of a fsck or similar for NTFS which is likely to be the filesystem on your Vista partition. I'm no Windows expert but if the tools that come with it don't work youre probably better of with starting from scratch anyway. I had a couple similar situations and after all starting from scratch would have been the faster way.

Have you tried mounting your Windows partition(s) from Ubuntu? Maybe you can at least rescue some files.

---

### Post by audiomick on 2010-01-05
Hi.
I can't help more than point to this page, which might help you get data out of the windows partition.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by Cheesemill on 2010-01-05
I wouldn't take any chances, I'd get a new drive.
You may well be able to claim on your home insurance for accidental damage to cover the cost.

---

### Post by campbuds on 2010-01-05
Ok, well I did already recover everything, Vista is just painful to reinstall and to top that off I would need to uninstall all the garbage that the Vaio comes with. THEN... Sony will take back the whole HD so I would need to reinstall Ubuntu also and tweak it back to the way I like including getting my webcam running again and run all the updates.

OH WELL... will do that tonight after work. Glad I didn't put too much work into it.

Question: Is there a reason Windows XP would not be able to see the NTFS partition ubuntu created on my external HD?

---

