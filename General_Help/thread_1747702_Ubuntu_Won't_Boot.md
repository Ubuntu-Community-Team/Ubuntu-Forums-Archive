---
title: "Ubuntu Won't Boot"
date: 2011-05-02
forum: General Help
---

### Post by goseph on 2011-05-02
Hi everybody,

Maverick Meerkat won't boot. I have tried removing the option of quiet boot and after a whirl of text flies by the splash screen is reached, after a few seconds just blackness indefinitely. Does anybody have any suggestions of what I can do?

Thanks for any help,


Luke

---

### Post by Rubi1200 on 2011-05-03
What graphics card do you have installed?

Have you recently updated/upgraded anything on the system?

Are you dual-booting?

Please do the following so we can get a better overview of the current state of the setup:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

