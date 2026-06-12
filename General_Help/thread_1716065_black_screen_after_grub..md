---
title: "black screen after grub."
date: 2011-03-27
forum: General Help
---

### Post by neba on 2011-03-27
I installed some updates and after I restarted ubuntu 10.10 I got the grub screen. After I hit enter all I got was a black screen. I left it alone for a few hours nothing changed. I I restarted and tried windows 7. that was having problems. I tried every option in the grub nothing will work, after messing with windows it started to work again, but ubuntu will not get past the black screen.
thank you for your help,
neba

---

### Post by Rubi1200 on 2011-03-28
Is this a Wubi install or is Ubuntu on its own partition?

First, run chkdsk in Windows:
[http://www.w7forums.com/use-chkdsk-check-disk-t448.html](http://www.w7forums.com/use-chkdsk-check-disk-t448.html)

Next, post the results of the boot info script from a LiveCD/USB:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

