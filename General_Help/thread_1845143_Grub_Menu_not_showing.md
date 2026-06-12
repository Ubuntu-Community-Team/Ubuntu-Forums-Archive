---
title: "Grub Menu not showing"
date: 2011-09-16
forum: General Help
---

### Post by cpu2007 on 2011-09-16
Hi there, I have a problem with the grub menu.
Everthing was working before, I could see the menu of ubuntu and windows 7 which I could choose from and select the OS I wanted to load.

I just reinstalled W7 and the grub menu disappeared.
I followed some tutorial here but no luck.

Used the command sudo grub install which worked.

After this I followed the instruction :

sudo grub

find /boot/grub/stage1  ( but this file is not found)

even using alternative procedures such as : 
sudo mount -t proc none /mnt/root/proc it doesn't work


Im running all this from the live cd and can see all the partitions, the W7, filesystem(which i believe is the one created by the live cd) and the installed ubuntu partion with all the files and documents there


How do I get my menu back?

Thanks

---

### Post by btindie on 2011-09-16
Have you tried following the suggestions in [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) ?

To do it manually when you're running the LiveCD you'll need to create a chroot environment and install GRUB from that so it gets setup correctly. [http://ubuntuforums.org/showthread.php?t=1499540](http://ubuntuforums.org/showthread.php?t=1499540)
[https://help.ubuntu.com/community/Grub2#ChRoot](https://help.ubuntu.com/community/Grub2#ChRoot)

When you reinstalled W7 it would have overwritten the MBR with its own.

---

### Post by drs305 on 2011-09-16
It looks like you are using procedures for Grub legacy, which will no longer work.

To restore Grub 2, boot the LiveCD and mount your Ubuntu partition. I'll use **sda5** but substitute the correct one.

```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda

```
Do not include the partition number in the second command.
Reboot and you should have Grub 2 back. Then run:
```
sudo update-grub
```
and your Windows OS should display in the menu.

If this doesn't fix it, let us know and we will have you post the RESULTS.txt contents (see the BIS link in my signature line).

---

### Post by cpu2007 on 2011-09-16
> **drs305 said:**
> It looks like you are using procedures for Grub legacy, which will no longer work.

To restore Grub 2, boot the LiveCD and mount your Ubuntu partition. I'll use **sda5** but substitute the correct one.

```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda

```Do not include the partition number in the second command.
Reboot and you should have Grub 2 back. Then run:
```
sudo update-grub
```and your Windows OS should display in the menu.

If this doesn't fix it, let us know and we will have you post the RESULTS.txt contents (see the BIS link in my signature line).

Thank you guys for the prompt reply.
@drs305, I have been searching a lot and everywhere the posted procedure were long and required the input of several line of codes.

but your worked perfectly.After the two lines I rebooted without the cd and the menu appeared again.

about the last line, do i require to update it or I can keep it like this?

---

### Post by drs305 on 2011-09-16
> **cpu2007 said:**
> 
about the last line, do i require to update it or I can keep it like this?

This 'update' command primarily causes Grub 2 to look at your partitions and update the entries in the grub menu. In some cases Grub 2 fails to find Windows the first time and the command needs to be run so Grub 2 can find it.  If your menu currently includes the OS's you want and it's working, you don't need to run the command. 

The command will also run automatically under certain circumstances, such as when a new kernel is introduced.

If everything is now good, you can mark the thread SOLVED if you wish using the 'Thread Tools' link at the top right of the first post.

Happy Ubuntu-ing !

---

### Post by cpu2007 on 2011-09-16
Thank you for the clear explanation.

---

