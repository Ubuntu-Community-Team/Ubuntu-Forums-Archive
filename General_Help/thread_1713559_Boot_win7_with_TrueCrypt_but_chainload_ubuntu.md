---
title: "Boot win7 with TrueCrypt but chainload ubuntu"
date: 2011-03-24
forum: General Help
---

### Post by &amp;Clyde on 2011-03-24
Hello,

With great help from the users here on the forums I managed to get grub installed and through this the option to boot into win7 or ubuntu.

The setup is set up as follows right now (my thread and the setup I have):
[http://ubuntuforums.org/showpost.php?p=10592465](http://ubuntuforums.org/showpost.php?p=10592465) (se posts #25 and #22).

Yesterday I installed TrueCrypt on my win7 OS. Naturally TC took over the MBR and now I can only load win7 by typing in the correct password. However, when I press ESC in TC bootloader, nothing happens (just an error of that no OS is found). How do I get ubuntu to load when I press ESC?

Thanks.

---

### Post by &amp;Clyde on 2011-03-24
Also, where does TC bootloader look when ESC is pressed? Should I have grub2 in /boot and it will find it automatically?

---

### Post by &amp;Clyde on 2011-03-25
Hello again,

tried something like this yesterday:
[http://ubuntuforums.org/showthread.php?t=761530](http://ubuntuforums.org/showthread.php?t=761530)


However, when I run 

```

sudo grub 
find /boot/grub/stage1 
or 
find /grub/stage1 

```I get an error of no found stage1's. Similarly I cannot run

```
install (hd0,*)/grub/stage1 (hd0) (hd0,*)/grub/stage2 0x8000 p
```Because it cannot find any disks (I do not remember the exact error message)

---

### Post by &amp;Clyde on 2011-03-25
Any ideas? :confused:

---

