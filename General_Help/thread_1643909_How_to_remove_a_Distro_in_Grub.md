---
title: "How to remove a Distro in Grub"
date: 2010-12-12
forum: General Help
---

### Post by tonyespo on 2010-12-12
Fixed

I can't figure out how to remove a Ubuntu distro in grub that I no long have installed.  I have Win 7, Ubuntu 10.4 installed but when I boot my grub menu shows Win 7, Ubuntu 10.4 and Ubuntu 10.10 that I have removed from my hard drive but still shows up in the menu.  I have been trying many commands in the terminal menu to edit grub but nothing shows me how to remove a menu entry.

Problem fixed Thanks Ubuntu Forum.



Help please,
Tony

---

### Post by Nissan_350Z on 2010-12-12
If i can remember correctly, try going to startup editor (download it from the application center) and delete it from there.. if you neeed more detailed instructions let me know and i will logon to my ubuntu and let you know. :D
It enables you to edit GRUB listings from startup..

---

### Post by oldfred on 2010-12-12
If you are booting with grub2. This should rescan system and only find current systems on computer.

```
sudo update-grub
```

---

### Post by tonyespo on 2010-12-12
> **oldfred said:**
> If you are booting with grub2. This should rescan system and only find current systems on computer.

```
sudo update-grub
```

Problem FIXED
Thanks your code fixed it perfectly.

---

### Post by jvmldv on 2011-01-07
I tried that but it didn't work for me.  I think that i still have all the old boot files. I don't know if thats a good idea to delete those files. please help

---

### Post by tredegar on 2011-01-07
**update-grub** will search all partitions for bootable operating systems, and offer a menu to boot any of them.

If you have tried **update-grub** and it is still offering a distro you do not want, you need to delete the partition that holds the distro you do not want before you run **update-grub**.

Be *_very_* careful that you do not delete the wrong partition, because you may regret it.

The commands **mount** and **fdisk -l** will help you determine which partitions are being used for what. Then you can delete the one you do not want, and then re-run **update-grub**

---

### Post by jvmldv on 2011-01-08
I have grub2 and i can remove my partitions right from synaptic package manager so thank you for your help

---

