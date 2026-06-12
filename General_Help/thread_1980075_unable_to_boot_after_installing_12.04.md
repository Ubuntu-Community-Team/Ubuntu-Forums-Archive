---
title: "unable to boot after installing 12.04"
date: 2012-05-14
forum: General Help
---

### Post by owners4life5 on 2012-05-14
i downloaded pangolin last night and upgraded what WAS my natty installation, choosing the option to erase all content. i already had windows 7 and windows xp installed along natty. installation went fine, after rebooting i can not choose any of my options, grub is missing.. i'm only offered a prompt that reads ```
grub>
```. what can i do?

---

### Post by wilee-nilee on 2012-05-14
Download this link extract it to your desktop and run the command. A results.txt is generated post it in the thread. This script gives a outline of your setup that is helpful for fixing this.

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)     

```
sudo bash ~/Desktop/bootinfoscript
```

---

### Post by owners4life5 on 2012-05-14
here you go!

---

### Post by wilee-nilee on 2012-05-14
> **owners4life5 said:**
> here you go!

So you have grub legacy in the sda HD where the ubuntu is installed, but none of the grub-legacy files in ubuntu, I think a load of grub 2 to the mbr will be fine. There is a boot-repair tool that is used by many that should work fine here is a link to the thread.  Make sure that the sda drive is before the sdb in the bios as well to be booted first

[http://ubuntuforums.org/showthread.php?t=1769482](http://ubuntuforums.org/showthread.php?t=1769482)

---

