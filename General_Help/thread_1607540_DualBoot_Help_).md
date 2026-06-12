---
title: "DualBoot Help :)"
date: 2010-10-27
forum: General Help
---

### Post by Don Ju4n on 2010-10-27
Hi everyone

I know this might be a realy odd question to ask here, but I want to learn how to uninstall an ubuntu copy on a dualboot machine. I installed ubuntu alongside with vista on my friend's computer cus she doesnt like opensource all that much. I am a newbie as well, with switching to ubuntu about 2 months ago. So my question is how to delete the linux partition without touching any vista files. I understand that i need the cd but i dont poses 1 because vista came preinstalled on the computer. So yeah, i have no way of reinstalling windows into the computer. Thanks everyone :)

---

### Post by Foxheadz on 2010-10-27
You can just use any partition editor and delete the ubuntu partition

---

### Post by Quackers on 2010-10-27
Unfortunately that will leave grub trying to boot a partition that isn't there and it will fail. So Windows won't boot either.
There are sites (google around) that offer Windows repair discs for download. You should download one, burn the image to disc and try booting from it first, to make sure it works. If all is ok you can then delete the Ubuntu partitions and then start from the Windows repair disc and repair the Windows bootloader.

---

