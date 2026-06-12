---
title: "help me reinstalling UBUNTU as a second OS!!"
date: 2009-07-25
forum: General Help
---

### Post by harsha.gadirjau on 2009-07-25
im new ti UBUNTU and im facing some problems in vista after installing Ubuntu.
And so i wanted to uninstall Ubuntu and reinstall it again. can anyone help me out how to do that..
NOTE:- I installed ubuntu from booting and not from windows..So i cant uninstall it from windows..

thanks
harsha.

---

### Post by merlinus on 2009-07-25
If you are experiencing problems with vista, how is reinstalling ubuntu going to help?

---

### Post by bodhi.zazen on 2009-07-25
Ubuntu does not need to be un-installed, simply re-install it and select manual partitioning.

If you are having problems booting Windows I suggest you de-bug that rather then re-install.

Ubutnu uses grub to boot and you can almost always simply configure or re-install grub.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by harsha.gadirjau on 2009-07-25
> **merlinus said:**
> If you are experiencing problems with vista, how is reinstalling ubuntu going to help?

my problem comes only after installing UBUNTU.
so i just want to do that..

---

### Post by harsha.gadirjau on 2009-07-25
> **bodhi.zazen said:**
> Ubuntu does not need to be un-installed, simply re-install it and select manual partitioning.

If you are having problems booting Windows I suggest you de-bug that rather then re-install.

Ubutnu uses grub to boot and you can almost always simply configure or re-install grub.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)


i want to uninstall it and want to increase the partition size for UBUNTU.
so i need it to be un install it first then reinstall it with much more space...

thanks
harsha.

---

### Post by merlinus on 2009-07-25
OK, clearer now.  I strongly suggest, however, that you use vista's disk management tool to shrink its partition, and defrag several times beforehand.

Then you can do a side-by-side or manual install of ubuntu.  But make sure the partition sizes are clearly specified.  You may have to use the sliders near the bottom of the screen to do so.

---

### Post by jocko on 2009-07-25
> **harsha.gadirjau said:**
> i want to uninstall it and want to increase the partition size for UBUNTU.
so i need it to be un install it first then reinstall it with much more space...

thanks
harsha.
You can't uninstall ubuntu (or any other operating system). Just boot the live cd, start the installer and when it comes to the partitioning part delete the ubuntu partition and make a new one the size you want it (and remember to format it to ext3, ext4 or any other linux file system and set it to be used as the root / file system).
If you need to shrink your windows partition, make sure you defragment it several times first to avoid data loss.

---

