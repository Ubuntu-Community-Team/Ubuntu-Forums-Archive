---
title: "Error 12: invalid device requested."
date: 2011-05-25
forum: General Help
---

### Post by plusnplus on 2011-05-25
Hi..,
I have message: error 12: invalid device requested.
It happen when i choose ubuntu partition.

before this error message the netbook run perfectly with dual boot.
ubuntu is 1st option
winXP is 2nd option from the list(maybe grub ?)

Since i want winxp as the 1st option instead ubuntu,
i change the file /boot/grub/menu.lst.
what exactly i change is just  cut and copy the winxp part to above ubuntu part.

if i press 'e' in ubuntu show:
root (hd0,6)
kernel /boot/bla..bla.bla..
initrd /boot/bla..bla.bla..
savedefault
makeactive
chainloader +1
quiet

if i press 'e' in winxp show:
root (hd0,0)

if i choose winxp it do nothing.
if i choose ubuntu it show message:
error 12: invalid device requested.
press any key to continue.

i tried to google it, but can not find the solution.

thanks for any help/ info.

---

### Post by Rubi1200 on 2011-05-27
Hi,

in order for us to get a better overview of what is going on, please do the following:

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

