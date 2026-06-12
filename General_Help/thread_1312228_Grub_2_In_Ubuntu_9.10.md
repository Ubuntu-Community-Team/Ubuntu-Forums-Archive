---
title: "Grub 2 In Ubuntu 9.10"
date: 2009-11-03
forum: General Help
---

### Post by Alterah on 2009-11-03
Hello,
I am fairly new to Ubuntu. I currently have it installed to try it out and it's helpful for a college class. However, I noticed that Grub loads and will automatically boot into Ubuntu (even though I have my hard drive with XP on it as the first boot device). I am simply wanting to change that default from Ubuntu to XP. I read I need to edit /etc/default/grub and select the appropriate entry. However, it won't let me change that file. I am fairly confident I should be an administrator. Thanks for any help. Let me know of any info you need.

---

### Post by darco on 2009-11-03
You can start here:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Lots to learn when it comes to grub2...

good luck


darco

---

### Post by DeMus on 2009-11-03
> **Alterah said:**
> Hello,
I am fairly new to Ubuntu. I currently have it installed to try it out and it's helpful for a college class. However, I noticed that Grub loads and will automatically boot into Ubuntu (even though I have my hard drive with XP on it as the first boot device). I am simply wanting to change that default from Ubuntu to XP. I read I need to edit /etc/default/grub and select the appropriate entry. However, it won't let me change that file. I am fairly confident I should be an administrator. Thanks for any help. Let me know of any info you need.

Open a terminal (Applications -> Accessories -> Terminal) and type
```
sudo gedit /etc/default/grub
```
Type your password. From now you are root (administrator)
Edit the file, save it and quit Gedit
Type
```
update-grub
```
to make the changes final
Reboot to see what you have done.

---

