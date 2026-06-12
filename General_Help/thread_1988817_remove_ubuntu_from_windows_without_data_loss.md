---
title: "remove ubuntu from windows without data loss"
date: 2012-05-28
forum: General Help
---

### Post by damms005 on 2012-05-28
This thread will definitely help a lot of us that are linux newbies. I've asked a kind guru and promised a solution to this, but it will be good if several opinions and/or experiences can help in drawing the best approach to doing this;
Synopsis:
I installed linux(ubuntu) from windows(wubi installer); although on another partition; but it seems that windows owns the bootloader/MBR. Thus, ubuntu can't boot without the windows OS.
Recently, I even formatted windows, but linux won't load at boot-startup(Although upon re-installation of windows, windows files were formatted but linux appeared again at boot-startup and its files were still intact)

Question is:
How can ubuntu be moved/reinstalled/installed such that it is not depending on windows to boot and all the objects it had when still in the "wubi installer format"(when it still depended on windows) is not affected(like applications, files, etc.)
Thanks you all.

---

### Post by na5h on 2012-05-28
Just back up your Ubuntu files and do a "real"* dual-boot installation (or use the entire hard-drive, if you don't need Windows any longer). Installing Ubuntu will also install the GRUB2 bootloader.

*as opposed to Wubi installation

---

### Post by ajgreeny on 2012-05-28
I have no windows and have never used wubi, so I can not speak from my own experience, but it should be possible to migrate a wubi installation to a normal partitioned installation.

See [https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi) and good luck.

---

