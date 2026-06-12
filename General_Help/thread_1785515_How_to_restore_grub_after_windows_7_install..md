---
title: "How to restore grub after windows 7 install."
date: 2011-06-18
forum: General Help
---

### Post by thecompgame on 2011-06-18
hey, iv looked around for the tutorials but none of them worked i keep getting errors.
Can someone just guide me from the top?
Thanks. Im posting this from the live CD.
edit: I just used a program that fixed everything for you.

---

### Post by Rubi1200 on 2011-06-18
Hi,
if you managed to fix the problem please mark this Solved using the Thread Tools near the top of the page.

If you still need help, do the following:
Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script which is in a zipped file. There is a link in my signature.
2. Once downloaded, move the boot info script by either copying or dragging and dropping the zipped folder onto the desktop and unzip the contents by using right-click Extract here.
3. Open the folder and copy the script to the desktop (you can also drag and drop if you like)
4. Open a terminal and run the following command

```
sudo bash ~/Desktop/boot_info_script.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

