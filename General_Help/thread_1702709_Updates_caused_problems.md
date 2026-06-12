---
title: "Updates caused problems"
date: 2011-03-08
forum: General Help
---

### Post by Sethathi on 2011-03-08
Hi,

I tried updating Ubuntu 10.10 and it froze during during the process so I decided to turn it off. Now, the problem is, it does not show the login screen but a only displays the name of my computer. 
How can I recovery it to an earlier period?

Thanks

---

### Post by kiyop on 2011-03-08
Push CTRL+ALT+F2, if tty2 is not shown.

If you are prompted to login, please type your user name and password to login.

If the end of the message is
$
then, type 
```
sudo dpkg --configure -a
```Push CTRL+ALT+F7 or CTRL+ALT+DEL.

---------------------------------------------------------
If you cannot see any prompt to login, restart and push shift key to display GRUB2 menu.
Select "Recovery".
Select "Root Shell".
then, type 
```
dpkg --configure -a
``````
exit
```Select normal boot or push CTRL+ALT+DEL.
---------------------------------------------------------

If you cannot enter to Recovery mode, boot with LiveCD.
"Application" -> " Accessory" -> "Terminal"

Type
```
sudo blkid
```and find the device file name of the partition where your Ubuntu was installed.
The device file name may be "/dev/[COLOR=red]sda5[/COLOR]" or so.

Type
```
sudo mount -t auto /dev/[COLOR=red]sda5[/COLOR] /mnt -o rw
sudo mount --bind /dev /mnt/dev
sudo mount --bind /sys /mnt/sys
sudo mount --bind /proc /mnt/proc
sudo chroot /mnt /bin/bash
```You should change /dev/[COLOR=red]sda5[/COLOR] to the correct device file name of your Ubuntu partition.
Prompt will be change to
root:/#

Type
```
dpkg --configure -a

exit
```Prompt will be change to
ubuntu@hogehoge:~$

Type
```
sudo umount /mnt/proc
sudo umount /mnt/sys
sudo umount /mnt/dev
sudo umount /mnt
```Restart and remove LiveCD.

---

