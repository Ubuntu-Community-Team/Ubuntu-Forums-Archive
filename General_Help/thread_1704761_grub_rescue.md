---
title: "grub rescue"
date: 2011-03-11
forum: General Help
---

### Post by unknown25 on 2011-03-11
guys pls help me.
i am getting this error at startup
grub rescue:

i have  an live cd and i have tried all the methods and i am just going in circles.i am not getting any proper or definite answer.i can just open my C drive from kubuntu and im getting hundreds of errors in konsole like permission denied or bad superblock etc......i tried all methods and none gave me any solution so pls help me....




pls help me with an definite solution

---

### Post by Rubi1200 on 2011-03-12
Hi,
please do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the _entire_ contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by unknown25 on 2011-03-15
Hey Thanks For The Help.But I Sorted It Out With The Help Of Windows xp Cd.

---

### Post by Rubi1200 on 2011-03-15
Okay, that is good news and I am glad you got it sorted out :-)

Care to elaborate on what the problem was, how it started, and why using the Windows CD helped solve the problem?

Thanks.

---

