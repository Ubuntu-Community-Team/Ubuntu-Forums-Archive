---
title: "Grub 2 Not Detecting Win7"
date: 2011-06-14
forum: General Help
---

### Post by FinalShot on 2011-06-14
I just reinstalled grub 2 to / from the live cd, ran sudo update-grub, but it didn't detect windows 7.

Partitions: 100GB - NTFS
200GB - Extended
100GB - Ext4 ( Media )
15GB - Ext 4 ( / )
6GB - Swap
80GB - Ext4 ( /home )

I installed Ubuntu first, then Windows 7.

---

### Post by Rubi1200 on 2011-06-14
Hi,
we need to get a better overview of what is where on the system.

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

### Post by FinalShot on 2011-06-14
Thanks, but I got it working, 2 possible ways.  Using 10.04 over 11.04, or the difference between "/mnt" and "/mnt/" is big.

I was using these commands:
```
sudo mount /dev/sda8 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

This worked:
```
sudo grub-install --root-directory=/mnt/ /dev/sda
```

I'm 90% confident it was the switch to 10.04, but who knows.

---

### Post by Rubi1200 on 2011-06-15
Glad to hear things worked out.

Enjoy :)

---

