---
title: "Transfer Data From Virtual Box to Host Machine"
date: 2012-04-13
forum: General Help
---

### Post by shad0w7 on 2012-04-13
Is it possible to set up a shared folder so I can install windows apps on the virtual box then copy them on my lubuntu host machine and run them with wine?

---

### Post by enkay009 on 2012-04-13
Sure. In the VMs configuration, add a shared folder and copy the files there. You may need to install the VirtualBox Gues Additions to your Windows VM first.

Or you could make a folder in your Windows VM shared, copy the files there, and then mount it from the host using CIFS/SMB.

---

### Post by lovinglinux on 2012-04-13
See [https://help.ubuntu.com/community/VirtualBox/SharedFolders](https://help.ubuntu.com/community/VirtualBox/SharedFolders)

---

