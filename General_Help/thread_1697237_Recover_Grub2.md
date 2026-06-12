---
title: "Recover Grub2"
date: 2011-02-28
forum: General Help
---

### Post by Zelda Hunter on 2011-02-28
I am trying to recover Grub2 after reinstalling Windows 7 on my computer (which always takes over everything). I downloaded the Ubuntu 10.10 image from [here]("http://www.ubuntu.com/desktop/get-ubuntu/download") and have mounted the image using the given instructions. 

After restarting my computer, changing the boot order, etc., the computer reboots and hangs at "Verifying DMI Pool Data............" I have done everything correctly, so what exactly is causing this problem? Should I restore Grub2 in some different way, then?

**Edit:** Fixed. Every time I spent an hour trying to fix something and finally make a post on a forum, the problem magically solves itself.

---

### Post by blueridgedog on 2011-02-28
> **Zelda Hunter said:**
> **Edit:** Fixed. Every time I spent an hour trying to fix something and finally make a post on a forum, the problem magically solves itself.

Try for a half hour next time :-)

Glad you have things sorted.  Grub is an odd duck for those from a windows background and implies a great deal of awareness of how a computers boots and loads an OS to tweak.  I am glad you worked it out.

---

### Post by Rubi1200 on 2011-03-01
Hi and welcome to the forums Zelda Hunter :)

If you would like us to take a closer look at your current setup, please do the following;

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

