---
title: "No root.disk"
date: 2011-10-13
forum: General Help
---

### Post by RapsonS on 2011-10-13
Hi guys

Recently my Ubuntu updated and now I am greeted with a grub prompt when I boot up.

I have tried everything, and it appears after running the boot info script, I am missing the root.disk. However, I have run a chkdsk and looked all over in hidden files and folders and it's nowhere to be seen!

Any ideas? Or will it have to be a fresh install :(

---

### Post by lolpenguin on 2011-10-13
You are using Ubuntu from the Windows UBuntu Installer (WUBI). root.disk is the virtual disk (dev/loop0) the system uses as its main partition. Because it is missing, you should perform a re-install of WUBI as it will re-create root.disk (1). Without root.disk, your WUBI installation cannot boot.
(1)Uninstall WUBI from Programs and Features (Windows 7) or Add or Remove Programs (Windows Vista, XP and earlier). After, start wubi.exe and recreate the installation.

Hope it helps!

---

### Post by RapsonS on 2011-10-13
lolpenguin,

Thanks very much for the reply. I take it this won't affect anything on my hard drive?

Sean

---

### Post by RapsonS on 2011-10-13
Scrap that. WUBI is not on my list of installed programs, all I have is Ubuntu in the list.

---

### Post by Techwarrior on 2011-10-13
i am having the same problem and i say having cause i have reinstalled about 5-6 times and get the same error every time  which is odd this is on my Laptop but it worked fine on my desktop not sure if this one is a dif version or not but im hoping there will be a fix for this :)

---

### Post by Mark Phelps on 2011-10-13
> **RapsonS said:**
> Scrap that. WUBI is not on my list of installed programs, all I have is Ubuntu in the list.

Wubi is the mechanism for installing Ubuntu; Ubuntu is what shows up in your programs list in Control Panel.

Simply remove Ubuntu -- like you would any other Windows app.

---

### Post by Rubi1200 on 2011-10-13
You can also manually remove Wubi:
[https://wiki.ubuntu.com/WubiGuide#How_do_I_manually_uninstall_Wubi.3F](https://wiki.ubuntu.com/WubiGuide#How_do_I_manually_uninstall_Wubi.3F)

By the way RapsonS I already responded to your support request in the Wubi Megathread. It would help all of us if you could confine your posts to one place rather than starting new threads on the same subject since it makes it harder for us to keep track of things.

Thanks for understanding.

---

