---
title: "problem in Dual-Boot!"
date: 2011-05-28
forum: General Help
---

### Post by DaYiM on 2011-05-28
Hello,
i installed Ubuntu on another partition from windows 7.
but before doing that i remember formating 100MB partition i think was called Boot "something"
thinking that i created this partition from my previous failures for installing Ubuntu,
now every time i restart the computer; i doesn't ask me about what to start!
it starts Ubuntu immediately!!!!!!!
" i even remember before installing Ubuntu; i couldn't start windows!"
maybe this is not Ubuntu related problem; but i hope anyone here well help me!
thanks & Best REGARDS

---

### Post by wgarcia on 2011-05-28
It seems you have used your entire disk for Ubuntu, therefore formatting your former Windows partition also. This is why Ubuntu starts directly, if it is the only operating system in the disk there is no sense of offering the Grub menu to choose which OS to start.

If you had important data there, there are ways of recovering data even after having formatted the disk I believe, but they are not easy.

---

### Post by DaYiM on 2011-05-28
thanks for your response,
i don't think is this the case,
because i have installed Ubuntu on different partition 
which is in different HardDisk, so when i took out the
HHD that Ubuntu from the laptop & started it, it says
that the windows can't start!!!
also i have checked while i am in Ubuntu:
that the HDD which windows on (Primary) is 95% full, 
which means all of my data & windows is still there
but can't be started, Thanks again! & please HELP!!!

---

### Post by Rubi1200 on 2011-05-28
Hi and welcome to the forums DaYiM :)

Let's get a better look at what is going on:

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

