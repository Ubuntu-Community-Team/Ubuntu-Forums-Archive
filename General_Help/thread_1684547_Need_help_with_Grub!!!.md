---
title: "Need help with Grub!!!"
date: 2011-02-09
forum: General Help
---

### Post by TechViking on 2011-02-09
Hey guys im really stumped i had Ubuntu running on dual boot with windows 7 on a separated HDD and i had to take the HDD out to put it into another machine and as soon as i booted my machine again i got this:

Error: No Such Device: 39a22a31-7229-467d-891e-e6a5b571d0a8
Grub Rescue>

I just want to remove grub completely as i plan to put Ubuntu on a virtual machine what do I do? any help would be most appreciated.

---

### Post by Rubi1200 on 2011-02-09
Hi and welcome to the forums :-)

Please do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the _entire_ contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by TechViking on 2011-04-29
Thanks very much, I have managed to resolve the issue :D

---

### Post by dirkoid on 2011-04-29
Hi,

For those of us who are interested could you post the solution?

---

