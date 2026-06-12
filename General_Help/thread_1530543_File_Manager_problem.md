---
title: "File Manager problem"
date: 2010-07-13
forum: General Help
---

### Post by TigrisAltaica on 2010-07-13
Hi. I just installed 9.10, and the "File Manager" seems to not be working. I cant get ubuntu to display a background picture on the desktop, and anything I put on the desktop is not selectable. If I try to access anything under the "Places" tab, it tries to open a window, which read "opening *whatever*" but nothing happens. I can access files via terminal just fine. Thanks.

---

### Post by kerry_s on 2010-07-13
sounds like you need to use the check disk feature on your installer, then try installing again.

---

### Post by TigrisAltaica on 2010-07-13
I'm kinda worried about re-installing since I'm running a dual boot machine and I don't think I have the windows disk any more. Is there anything else I could do? Or could somebody point me towards a tutorial for making a clean re install that doesn't run the risk of blasting the windows partition? Thanks.

---

### Post by gadolinio on 2010-07-13
Mmm I'd try to reinstall nautilus, and if it doesn't work consider reinstalling ubuntu, as you have a clean new system, right?

---

### Post by TigrisAltaica on 2010-07-13
This is going to sound silly. How do I re-install nautilus? Thanks.

---

### Post by TigrisAltaica on 2010-07-14
Bump!

---

### Post by m4tic on 2010-07-14
Well since you said you've just installed ubuntu, i woud say you should reinstall again. Downloading Nautilous is going to cost you unless you don't have a problem with your bandwidth. Hey have you tried restarting the computer? If you cannot get windows to boot enter this
```
sudo update-grub2
```

---

### Post by TigrisAltaica on 2010-07-14
What I'm worried about is messing up the windows install. How do I re install ubuntu in the same partition as the current install? Thanks.

---

### Post by m4tic on 2010-07-14
> **TigrisAltaica said:**
> What I'm worried about is messing up the windows install. How do I re install ubuntu in the same partition as the current install? Thanks.
 
When you reach the partitioning stage in the install, on the bottom choose "custom partitioning" then select the ext4 file system and choose edit, on the mount point options put it to "/" and save and install. It's really streight forward. "/" means root, this is where the OS installs iitself on.  Similar to windows's C drive

---

### Post by TigrisAltaica on 2010-07-14
Thank you, will do.

---

