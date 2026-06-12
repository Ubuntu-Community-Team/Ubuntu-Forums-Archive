---
title: "help me boot windows 7 with ubuntu"
date: 2011-03-21
forum: General Help
---

### Post by 2asem on 2011-03-21
help
i had windows7 64 bit on my computer 
i made a new partition so i coul install ubuntu 
but when i did i coudnt boot to windows 
when i pick windows 7 an error appears saying no such partition then a grub rescue 
plz help i really need to boot to windows

---

### Post by Rubi1200 on 2011-03-21
Hi and welcome to the forums :-)

Please do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

