---
title: "How do I get into menu.lst and fstab from live cd?"
date: 2010-11-28
forum: General Help
---

### Post by Boris and Bailey on 2010-11-28
It looks like my problems with Error 15 are because I have UUID entries instead of root entries.

How can I access menu.lst and fstab using a live cd so I can edit the entries?

It looks like these files are on sda1.

---

### Post by nothingspecial on 2010-11-28
from live cd terminal

```
sudo mkdir /media/ubuntu
```
```

sudo mount -t ext4 /dev/sda1 /media/ubuntu
```

```
gksudo gedit /media/ubuntu/etc/fstab
```

make your changes

save, close

You shouldn`t have a menu.lst unless you are using an old version of ubuntu, in which case you might have to change ext4 to ext3 in the mount command.

Then ```
gksudo gedit /media/ubuntu/boot/grub/menu.lst
```

make changes

save close

---

### Post by oldfred on 2010-11-28
Error 15 is usually a conflict between old grub legacy and grub2. Do you have parts of each installed.

To see what is where:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] here [ /code] tags.

chroot & grub uninstall & reinstall
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by nothingspecial on 2010-11-28
> **oldfred said:**
> Error 15 is usually a conflict between old grub legacy and grub2. Do you have parts of each installed.

To see what is where:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] here [ /code] tags.

chroot & grub uninstall & reinstall
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)


I tried to answer your question :p

However, I`d go with what oldfred said :D

---

