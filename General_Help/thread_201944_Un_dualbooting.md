---
title: "Un dualbooting"
date: 2006-06-22
forum: General Help
---

### Post by Hawkeye05 on 2006-06-22
i have a dualboot going with Unbuntu 5.04 and XP Pro, id like the uninstall Ubuntu and the Dual Boot software without Deleting my windows files, ive tried before just deleting and reformatting to Ubuntu partition but that time nothing would boot, i have very little expierience at command lines etc.  

Thanks in advance

---

### Post by ajgreeny on 2006-06-22
If you delete the ubuntu partition you get rid of grub, or the menu.lst file that grub (on your windows partition's master boot record [MBR] by default).  That is why you can't now boot anything.

You will need to use your winxp install CD and use the recovery module to fixmbr.  Just google for "fixmbr" if you are not sure how to do it;  there are lots of sites in all languages to tell you how in detail.

---

### Post by Hawkeye05 on 2006-06-22
oh you mustve misunderstood thats what happened last time, i had to completely repartition/reformat the entire drive, im wondering how to do it the right way this time

---

