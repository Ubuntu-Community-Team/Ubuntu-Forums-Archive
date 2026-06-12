---
title: "Grub dont work"
date: 2010-06-23
forum: General Help
---

### Post by HannuMR on 2010-06-23
Ubuntu 10.04 was in small slave-disk, and I put other bigger disk same type IDE/ATA.
In first start I get message: "no such device....., grub rescue."
Anyway, I make installation in this disk and and now after start message is: "error: out of disk, grub rescue."
So now I can not use master/XP and no slave/Ubuntu.
Ideas?
Thanks.

---

### Post by dino99 on 2010-06-23
installing:

mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14) 

more grub info below

---

### Post by oldfred on 2010-06-23
Which disk is master & slave. Does your BIOS let you choose boot drive or do you have to use the cable select or jumpers on IDE drives to choose boot drive?

To see your entire configuration:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.

---

### Post by HannuMR on 2010-06-23
Sorry guys.

My stupid mistake.
Jumper was in the wrong place, so I had two master-disks, and grub did not work.
Now second disk is slave, and ewerything works.

---

