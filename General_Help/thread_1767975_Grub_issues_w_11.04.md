---
title: "Grub issues w/ 11.04"
date: 2011-05-26
forum: General Help
---

### Post by ashgray on 2011-05-26
I dual boot Windows 7 and Ubuntu, and recently I updated from 10.04 to 11.04 via live cd. However, I now get the grub rescue prompt instead of the normal grub menu when I boot my computer. Any advice?

---

### Post by Rubi1200 on 2011-05-27
Hi and welcome to the forums :-)

For us to get a better picture of what is going on, please do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script which is in a zipped file. There is a link in my signature.
2. Once downloaded, move the boot info script by either copying or dragging and dropping the zipped folder onto the desktop and unzip the contents by using right-click Extract here.
3. Open the folder and copy the script to the desktop (you can also drag and drop if you like)
4. Open a terminal and run the following command

```
sudo bash ~/Desktop/boot_info_script.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

(off-topic; please let me know if the instructions I gave are clear and easy to follow, thanks)

---

