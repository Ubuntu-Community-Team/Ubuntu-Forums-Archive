---
title: "Virtual Box moving files between OS and virtual box"
date: 2010-05-14
forum: General Help
---

### Post by planekrazy57 on 2010-05-14
I want to install Virtual Box on my Linux version 9.10. If I install Windows Vista in Virtual Box, can I transfer files from Windows Vista in Virtual Box to my Linux 9.10 OS?

---

### Post by NightwishFan on 2010-05-15
There probably is a way, but none that I know of. I work this around by using my ubuntu-one to move files **from** the virtual windows/linux and I burn a data iso of files I want to move **into** my virtual system and mount it in virtualbox.

---

### Post by Ginsu543 on 2010-05-15
You can easily do this by setting up shared folders. When you set up a VM in VirtualBox, there is an option to add shared folders. It can be any folder recognized by the Ubuntu OS (so it can be a folder in your /home directory or a folder from an NTFS partition). Once you add the shared folder, you can then boot into Vista and look under My Network Places. If you search through your Entire Network, you should see VirtualBox Shared Folders. You can right-click on each and choose the "Map Network Drive" menu item. After that, you should be able to see and access each folder under My Computer. Whatever you put in those folders will be accessible by both Ubuntu and Vista.

---

### Post by _0R10N on 2010-05-15
> **Ginsu543 said:**
> You can easily do this by setting up shared folders. When you set up a VM in VirtualBox, there is an option to add shared folders. It can be any folder recognized by the Ubuntu OS (so it can be a folder in your /home directory or a folder from an NTFS partition). Once you add the shared folder, you can then boot into Vista and look under My Network Places. If you search through your Entire Network, you should see VirtualBox Shared Folders. You can right-click on each and choose the "Map Network Drive" menu item. After that, you should be able to see and access each folder under My Computer. Whatever you put in those folders will be accessible by both Ubuntu and Vista.

Yep! this approach is definitely the easier, more elegant and simple!

---

### Post by kio_http on 2010-05-15
> **Ginsu543 said:**
> You can easily do this by setting up shared folders. When you set up a VM in VirtualBox, there is an option to add shared folders. It can be any folder recognized by the Ubuntu OS (so it can be a folder in your /home directory or a folder from an NTFS partition). Once you add the shared folder, you can then boot into Vista and look under My Network Places. If you search through your Entire Network, you should see VirtualBox Shared Folders. You can right-click on each and choose the "Map Network Drive" menu item. After that, you should be able to see and access each folder under My Computer. Whatever you put in those folders will be accessible by both Ubuntu and Vista.

This will work. Note the server is //vboxsvr

---

### Post by gadolinio on 2010-05-15
> **Ginsu543 said:**
> You can easily do this by setting up shared folders. When you set up a VM in VirtualBox, there is an option to add shared folders. It can be any folder recognized by the Ubuntu OS (so it can be a folder in your /home directory or a folder from an NTFS partition). Once you add the shared folder, you can then boot into Vista and look under My Network Places. If you search through your Entire Network, you should see VirtualBox Shared Folders. You can right-click on each and choose the "Map Network Drive" menu item. After that, you should be able to see and access each folder under My Computer. Whatever you put in those folders will be accessible by both Ubuntu and Vista.
That's right. You can give a drive letter to the shared folder, like D:\, and access it anytime to move files from one system to the other.

---

### Post by planekrazy57 on 2010-05-18
Thanks Ginsu543. I appreciate the help. Also thanks to the other members for there responses and info. It is so great to get this kind of response and quality of help/information. This forum is great.

---

### Post by gadolinio on 2010-05-18
> **planekrazy57 said:**
> This forum is great.
Indeed :D

---

