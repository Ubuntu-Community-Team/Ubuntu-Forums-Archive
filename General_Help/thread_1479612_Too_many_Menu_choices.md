---
title: "Too many Menu choices"
date: 2010-05-10
forum: General Help
---

### Post by planekrazy57 on 2010-05-10
after many updates to 9.10, my main boot menu has many entries for the different update versions of Linux. Is there a way to edit the boot menu so I see the latest updated versions of Linux to boot from and not all of them? Appreciate any help you can give. Not afraid to get down and dirty in the software. Just need to know how. Thanks.

---

### Post by Dessicus on 2010-05-10
Try this: [http://ubuntuforums.org/showpost.php?p=8057950&postcount=8](http://ubuntuforums.org/showpost.php?p=8057950&postcount=8)

---

### Post by WRDN on 2010-05-10
What I usually do, is open the GRUB menu file:

```
gksudo gedit /boot/grub/menu.lst
```

Then put a hash # before the Title lines for the entries you are not interested in (or remove them completely).

---

### Post by Padapwa on 2010-05-10
> **planekrazy57 said:**
> after many updates to 9.10, my main boot menu has many entries for the different update versions of Linux. Is there a way to edit the boot menu so I see the latest updated versions of Linux to boot from and not all of them? Appreciate any help you can give. Not afraid to get down and dirty in the software. Just need to know how. Thanks.

Sure, i'm not sure which editor you like best so i'm going to give the instructions for VIM

sudo vim /boot/grub/menu.lst

Remove all lines you don't want. (if you are not familiar with VIM, just move the cursor to the line you want to delete by using your arrow keys and press "d" twice.

:wq (if you are not familiar with VIM you should become familiar with VIM, it's going to help you out a lot in all kinds of systems, you can even install it in windows. Anyways ":" is pressed when you want to use functions and not write within your document, after pressing that you press "w" for write and "q" for quit since youre done and hit enter to get you back to the prompt)

That is all.

---

### Post by Dessicus on 2010-05-10
9.10 uses grub2 there is no menu.lst
The best way is to remove the old linux images in synaptic

[More info on grub2]("https://wiki.ubuntu.com/Grub2")

---

### Post by oldfred on 2010-05-10
If the 9.10 is an upgrade it may still have grub legacy. So editing the menu.lst is possible for those with upgrades.

Dessicus recommendation of deleting old kernels works for grub legacy and grub2.

A third choice is just to not display the kernels. If you have a fair amount of disk space they do not take much room. In grub legacy there was a setting for howmany to display. In grub2 you can edit */etc/grub.d/10_linux*:

includes line to limit display to two
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showpost.php?p=8082954&postcount=1](http://ubuntuforums.org/showpost.php?p=8082954&postcount=1)

---

### Post by planekrazy57 on 2010-05-10
Thanks. I used the synaptic package manager to remove the old kernels. I appreciate the quick response and the number of options to remove the old kernels.

---

