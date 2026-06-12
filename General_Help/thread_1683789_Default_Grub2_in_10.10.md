---
title: "Default Grub2 in 10.10"
date: 2011-02-08
forum: General Help
---

### Post by flebber on 2011-02-08
In the latest ubuntu install where is grub installed by default? I have a feeling that it doesn't install to the mbr anymore is that correct?

---

### Post by Rubi1200 on 2011-02-08
By default, GRUB is installed to the MBR of the drive.

Are you having problems with it?

If yes, do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

