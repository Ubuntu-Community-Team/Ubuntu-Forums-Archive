---
title: "Recovery Data....HELP GAN"
date: 2011-05-21
forum: General Help
---

### Post by dzakil on 2011-05-21
Hi all,

anyone know how to recovery data? cuz I've del my file(film)

Help me............
:confused::confused::confused:

---

### Post by prshah on 2011-05-21
> **dzakil said:**
> [SIZE=3]anyone know how to recovery data? cuz I've del my file(film)

You can use photorec ; it's in the repos (install it from software center). It has the best chance of recovering deleted files, but it will recover tons of files.

Please post back if you want details on how to use photorec.

---

### Post by bdoe on 2011-05-21
How did you delete your file exactly? If you just simply deleted it from within Nautilus (the graphical file manager), then your "deleted" file is sitting safely in your trashcan. Just open the trashcan, find your file, select it, and click "Restore selected items".

If you deleted your file in terminal, emptied your trash, or deleted it with Shift+Del key combination in Nautilus, then your file is truly deleted, and you'll need an undelete tool to recover it - assuming you haven't written anything else to your hard drive.

---

### Post by mörgæs on 2011-05-21
First of all: Stop using the hard drive, which can make the problem worse. 

Study the suggestions in the posts above when booted into a live environment.

---

### Post by dzakil on 2011-05-21
> **bdoe said:**
> How did you delete your file exactly? If you just simply deleted it from within Nautilus (the graphical file manager), then your "deleted" file is sitting safely in your trashcan. Just open the trashcan, find your file, select it, and click "Restore selected items".

If you deleted your file in terminal, emptied your trash, or deleted it with Shift+Del key combination in Nautilus, then your file is truly deleted, and you'll need an undelete tool to recover it - assuming you haven't written anything else to your hard drive.

I've deleted my file with clicking empty trash.....

---

### Post by dzakil on 2011-05-21
> **prshah said:**
> You can use photorec ; it's in the repos (install it from software center). It has the best chance of recovering deleted files, but it will recover tons of files.

Please post back if you want details on how to use photorec.

I don't found photorec in software center. and I've installed recuva(software recovery for windows). I've opened it with wine. but, This software has failed to recovery my data.

---

### Post by ambdeep on 2011-05-21
you can also  try extundelete. it is the simplest software i found for this purpose and it works like a charm.

---

### Post by prshah on 2011-05-21
> **dzakil said:**
> I don't found photorec in software center

Windows recovery software will not help you in any way. Photorec is present in the repositories in the package "testdisk". Searching for PhotoRec will present the testdisk package in the software center.

However, you can also install it by opening a terminal (Applications-Accesories-Terminal) and giving the command```
sudo apt-get install testdisk
``` or by just clicking [here]("apt://testdisk")

Please post back if you need any further assistance.

---

