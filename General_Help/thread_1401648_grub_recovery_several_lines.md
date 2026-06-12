---
title: "grub recovery several lines"
date: 2010-02-08
forum: General Help
---

### Post by gchand7 on 2010-02-08
I have a dual boot system with Ubuntu 9.10 and 7. When I boot up the computer it does the normal screen where you use the up down arrow to select but I seem to have several GRUB lines. What causes this and can I delete some of these or should I just live with them.  Thanks guys

---

### Post by gchand7 on 2010-02-10
heres a pict.

---

### Post by shabs on 2010-02-10
Well that should be as simple as editing the /boot/grub/menu.lst file and commenting the options that you don't want seen. 

Shabs.

---

### Post by mcduck on 2010-02-10
Nothign special there.

When you get a kernel update the new version doesn't overwrite the old one, it's installed aliongside any olde kernel versiosn you have. This allows you tp test the new kernel to make sure it works correctly on your system, and if there are any problems you can still select to boot into the old kernel and get a working system.

Anyway, after you've used the new kernel version for a while you can simply uninstall the old one and it will automatically be removed from the Grub menu as well.

(editing the menu.lst doesn't work for 9.10, it doesn't even have such a file. Besides, that would take the same amount of work that unisnatllign the lld kernel takes, but you'd still have the actual kernel wasting your disk space.. So just uninstall the old version instead..)

---

### Post by shabs on 2010-02-10
Ah ok. Thats news to me. Thanks :)

---

### Post by gchand7 on 2010-02-10
Thanks guys I think I'll live with it! I'm still a newbie and am afraid to go messing around with stuff like that.

---

### Post by mcduck on 2010-02-10
> **gchand7 said:**
> Thanks guys I think I'll live with it! I'm still a newbie and am afraid to go messing around with stuff like that.

If you get any more than 2 kernels there, the Computer Janitor (In System/Administration menu) will automatically remove them for you. But it will always leave one older kernel version around (most likely because so many people like to have one).

---

