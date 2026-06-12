---
title: "Make sure all necessary files desktop are installed."
date: 2012-03-11
forum: General Help
---

### Post by ReptilianShadow on 2012-03-11
Sorry if the title is a bit unclear, but I'm not sure how to explain it in short.

Playing around with wine, I decided to install wine1.3 as it's the newer version to the default wine1.2, I noticed some incompatibilities with some programs, so I decided to go back to wine1.2.

I did ```
sudo apt-get remove wine1.3
```
and nearly uninstalled many packages. I killed (sudo pkill) the dpkg session to stop it, and used ```
sudo dpkg --configure -a
``` as prompted when I tried to re-install wine1.3 to try and amend any issues that might have risen because of my screw up.

How can I make sure that no important packages were removed or damaged?

I'm a bit worried to turn off my computer after this, I've experienced something like this before, and it left me with an odd color, slow flashing screen after reboot.

Any is advice would be helpful, 

Thank You,
ReptilianShadow

---

### Post by 2F4U on 2012-03-11
During the remove process, apt-get should have given you a list of applications that are going to be removed. You should check that list if the programs are still there and, if not, reinstall missing programs.

---

### Post by mcduck on 2012-03-11
There are metapackages for each desktop environment, made to make sure all the things that belong to the default setup are installed. So for normal Ubuntu having the "ubuntu-desktop" metapackage will guarantee you have everything that is included in the default Ubuntu setup.

"kubuntu-desktop" serves the same purpose on Kubuntu, and of course there are also "xubuntu-desktop", "lubuntu-desktop" and "edubuntu-desktop".

(These will not include any additional packages you may have had to install to get Ubuntu work in the first place, so if your system needs any proprietary graphics drivers etc. you'll have to check those yourself).

However, removing Wine using that exact command really shouldn't remove any of the default packages. None of them depends on Wine.

---

### Post by ReptilianShadow on 2012-03-11
Thank you very much for the info. Everything [still] works fine. If only I knew about those meta-packages the two previous times I messed up ;).
But thanks again.

---

