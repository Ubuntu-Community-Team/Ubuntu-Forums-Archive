---
title: "A question about grub2 decoration using BURG"
date: 2009-11-27
forum: General Help
---

### Post by lwq316 on 2009-11-27
I've followed this guide[http://ubuntuguide.net/decorate-grub-2-boot-loader-using-burg/comment-page-1#comment-2121](http://ubuntuguide.net/decorate-grub-2-boot-loader-using-burg/comment-page-1#comment-2121)and make it successfully.But I want to know how to add OS logo icons to the panel.Like pictures here:[http://grub.gibibit.com/Themes](http://grub.gibibit.com/Themes).Anyone could tell me detailedly? I'm a green hand.
My OS release is Ubuntu9.10 and boot by grub2.

---

### Post by cfalzone on 2010-06-10
I know that I'm answering this really late in the game, but maybe you are still wondering how to do this.

In order to get BURG to use only icons you need to make sure you have BURG installed to the MBR (master boot record).  Installing BURG for the first time will ask you if you want to do this.

Once it is installed you should reboot and when the BURG menu appears simply press "T" and you may choose between preset themes (pretty much all that you can find online are included by default).

Press "R" to change resolution for your display.

Navigate to ```
/boot/burg/themes
``` if you want to make modifications to any theme folders.  After modification you should ```
sudo update-burg
``` to update the BURG menu.

---

