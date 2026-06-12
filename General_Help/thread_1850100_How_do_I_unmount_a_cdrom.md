---
title: "How do I unmount a cdrom?"
date: 2011-09-25
forum: General Help
---

### Post by BlackoutWorm on 2011-09-25
Hey. I mounted a iso as a cdrom to install Counter Strike Condition Zero, but now when I have installed it I don't need to have the cd mounted anymore.
When I try to unmount it from the computer folder, it says I have to bee root.
Seriously? I have to be root to unmount a cdrom drive?
That is so gay.
Anyhow, how do I unmount it?
Also, plz fix this issue before the release of 11.10.

---

### Post by garvinrick4 on 2011-09-25
eject /dev/sr0
If you were not so sarcastic you would get more help here.
You are really showing how immature you are. Have a nice day BlackoutWorm.

---

### Post by BlackoutWorm on 2011-09-25
> **garvinrick4 said:**
> You can just eject it if that is what you want.
eject /dev/sr0
Thanks but that's not what I meant.
It's a mounted iso file. Not a cd device.
I used furius iso mounter, and for some reason it doesn't include and unmount function. Stupid software.
So I need to unmount it myself.

When I try to unmount it from the computer folder, it says:

umount: /home/thobias/Counter_Strike_Condition_Zero_CD2_ISO is not in the fstab (and you are not root)

---

### Post by BlackoutWorm on 2011-09-25
Problem solved (somewhat).
But I had to do it from the terminal thing.
I did "sudo umount /home/thobias/Counter_Strike_Condition_Zero_CD1_ISO"
But again, please fix it so it doesn't need root permission. Because then it's not possible to do this from the computer folder, which again makes this very un-userfriendly. Just saying.

---

