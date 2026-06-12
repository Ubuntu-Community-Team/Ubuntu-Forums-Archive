---
title: "Cant access ubuntu on 2nd harddrive after reinstall of xp"
date: 2011-01-05
forum: General Help
---

### Post by hoggsy on 2011-01-05
I have two hard drives one running Ubuntu 10.04 and the other XP (only for itunes and gaming) but earlier today i needed to reinstall xp as its windows and got bored of working properly and i am now unable to access the ubuntu harddrive as grub was written to the windows mbr.
Now i would of normally just reinstalled Ubuntu and gone from there but as i was trying to be clever i copied my itunes folder over and i dont really wont to lose this.
So two questions;
1) How can i add the Ubuntu harddrive back to the boot options ?
2) Or how can i get the itunes folder off the Ubuntu install using a live disk or from xp?

---

### Post by hoggsy on 2011-01-06
Anyone got an idea ?

---

### Post by Quackers on 2011-01-06
If grub is also installed to the mbr of your Ubuntu hard drive change your bios to boot from that hard drive first. Then if Ubuntu boots up open a terminal and run ```
sudo update-grub
```
If grub is not installed to the Ubuntu hard drive you would need to re-install grub to the mbr of the Windows drive. If that is the case, please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by ubun2warrior on 2011-01-06
hi

you can simply boot with a live ubuntu cd or usb and then back up ur itunes folder to some other pendrive or the windows hard drive..

and then you may reinstall ubuntu if you want..

regards

---

