---
title: "Grub doesn't detect xp/7"
date: 2011-11-12
forum: General Help
---

### Post by kirill578 on 2011-11-12
I had Ubuntu 11.10 and windows 7 installed on my HD on different parttion,I had to install XP so i devided the window's 7 parttion in to to and installed it. Next I retored the grub, but update-grub could not deteced windows xp, so I tried to boot into my windows 7, However i found my self booting into XP. 

My ubuntu is located in dev\sda2
7 - dev\sda3
xp - dev\sda4

Any suggestion?

---

### Post by Mark Phelps on 2011-11-12
I don't know if this will work -- but it's worth a try ...

Boot from an Ubuntu desktop CD.  Choose the Try Ubuntu option.

Open a terminal and enter "sudo update-grub".

Watch the messages and see if it detects Windows 7.

Reboot the PC.

Now, when you choose Windows 7, you should see an entry in the menu for XP.

If you get to Win7 but there is no XP entry, then do the following (GRUB won't be able to generate a separate entry for XP, so THIS is the way to fix that:
1) Go to NeoSmart technlogies website (from inside Win7) and download EasyBCD
2) Install EasyBCD
3) Run that and select the optio to Edit the boot menu.  When it opens, see what entries are there.  I suspect there will not be an entry for XP.
4) Select the option to Add and entry -- fill out the fields and use the pulldown to create an entry for XP.
5) Save the result

Reboot, choose the option for Win7 in GRUB.

Now, you should see a text menu (from Windows) that includes Windows 7, and another entry, probably something like Older version (or something like that).  When you select this other entry, you should boot into XP.

You can also then go back into Win7, run EasyBCD again, and Edit the boot menu to change the wording for the Other operating system to say Windows XP.

Good Luck

---

