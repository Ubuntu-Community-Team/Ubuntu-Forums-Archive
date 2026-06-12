---
title: "Help!Grub doesn`t show ubuntu..."
date: 2010-02-28
forum: General Help
---

### Post by dsouza95 on 2010-02-28
My problems started when i discovered that I could install Neverwinter Nights in ubuntu. Lot`s of hacks later, I managed to install it but it was slow. I assumed that was because my video hardware was not updated, so I updated it and picked ubuntu`s suggestion on what 'firmware' to use(needed 3D graphics accelerator)... That`s when things went wrong. Ubuntu was starting, but very strange, (The **** Nvidia went nuts). So I took my ubuntu 9.10 disk(My current version) and marked 'repair system problems' or something similiar...Lots of words later, it said some files would be deleted, I said 'Y'. Rebooted...Ok, now what the ****, ubuntu is not in grub anymore. I can see the system files(not sure there are all of them)...Help please I`ve searched but most methods don't work for me(Probably cause my brother did the partition thing).

---

### Post by Richard1979 on 2010-02-28
Just a hint: when it says it's going to delete something, you pay attention.
Anyway, if you can get into Ubuntu from the Live CD, mount your root disk (click on it in the Places menu), then type "sudo update-grub".

---

