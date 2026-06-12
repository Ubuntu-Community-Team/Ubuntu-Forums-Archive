---
title: "[URGENT!!!] root.disk Can't be Read"
date: 2012-04-22
forum: General Help
---

### Post by MaestroMaestro on 2012-04-22
Okay, so I've been using WUBI for a while. The other day, the computer froze and I was forced to restart because absolutely nothing worked. Now, I can't boot Ubuntu anymore. It stays at a purple screen forever. SO, I tried to use explore2fs to recover some VERY important files from root.disk. But, it showed that there was nothing in it. Trying to open with 7zip says that it's unreadable and corrupt. 

PLEASE help, I really need some of those files.

P.S. in Windows Explorer it says that it's 29 GB, but it still shows nothing in explore2fs

---

### Post by Karlchen on 2012-04-22
Hello, MaestroMaestro.

In case the underlying Windows NTFS filesystem is damaged, you will have to make sure you run a **chkdsk /f** on it and fix all errors prior to procceding and trying to check/repair the Wubi root.disk.

Have a close look at [**this thread**]("http://ubuntuforums.org/showpost.php?p=9932369&postcount=5"), please. The most relevant part is about loop mounting the Wubi root.disk and about running an fcsk on it: [**loop mount the wubi root.disk**]("https://wiki.ubuntu.com/WubiGuide#How_can_I_access_my_Wubi_install_and_repair_my_install_if_it_won.27t_boot.3F")

[**How can I access my Wubi install and repair my install if it won't boot?**]("https://wiki.ubuntu.com/WubiGuide#How_can_I_access_my_Wubi_install_and_repair_my_install_if_it_won.27t_boot.3F")

Hope this instruction will help you make your Wubi installation bootable and usable again. Else it should help mount the filesystem inside the root.disk file and allow you to copy all relevant data to an external medium e.g. thus preventing you from losing all your data.

Good luck,
Karl

---

### Post by Karlchen on 2012-04-23
Hello, MaestroMaestro.

There seems to be some similarity between your old thread here: [**URGENT: Won't boot after Windows Update**]("http://ubuntuforums.org/showthread.php?t=1928648") , and your current thread: In both cases the root.disk of the Wubi installation seems to have been damaged.

Is this thread here actually your old thread in reposted form? You have never posted back over there in the old thread. So I wonder what happened back in February and how you solved the reported problem. Forestpiskie pointed you to the same article that I suggested, too.

Kind regards,
Karl

---

