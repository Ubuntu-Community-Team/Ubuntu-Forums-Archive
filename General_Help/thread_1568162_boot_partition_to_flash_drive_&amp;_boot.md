---
title: "/boot partition to flash drive &amp; boot"
date: 2010-09-04
forum: General Help
---

### Post by Gitanes on 2010-09-04
Hello.  I've got /boot installed to a usb flash drive but I've been unable to boot from it.  I select the drive from boot options, and when I try to boot, it just takes me to a screen saying "error: no such device" followed by a long string of numbers and letters (an identifying number no doubt) and a grub rescue prompt.

I'm under the impression, from another posting, that my grub.cfg file needs to be edited for this setup to work.  I notice references in that file to (hd0,1) which would be my Windows partition and (Hd1,1) which should be the flash drive that I installed /boot to.  The Ubuntu partition on my HD is an encrypted lvm.

What do I need to edit in my grub.cfg file to get this to work or what other things must I do to get it to work?

Thanks.

---

### Post by jeight on 2010-09-04
Common mistake... on the last step on install make sure you choose advanced options and make grub install on the flash drive. Otherwise your flash drive has no bootloader.

---

### Post by garvinrick4 on 2010-09-04
If you can put your flash drive in and boot off of a live cd. So now in places you can see your hdd and your usb flash drive. open gparted in live cd and right click on flash drive if sdb or sdc whatever it is. Now give it a label lets say lucid for this. Click green arrow and apply the label. Now open a terminal and: Copy and Paste one at a time.
```
sudo mkdir /media/lucid
``````
sudo mount /dev/sdb2 /media/lucid
``````
sudo grub-install --recheck --root-directory=/media/lucid /dev/sdb
``````
sudo umount /media/lucid
```Given your label is lucid and your Ubuntu install is in sdb2   (use what yours are)

1.You have made a directory for your flash drive
2.You have mounted your drive
3.You have put your grub into mbr  which is always sda, sdb, sdc whichever drive is never sda1 or sda2  just sda or sdb , if you are using /boot partition it will put it in right spot do not put in yourself. Just sda or sdb and so on.
4.You have unmounted your drive

Now reboot into flash drive (remove cd) and run:
```
sudo update-grub
```

---

### Post by Gitanes on 2010-09-05
Thanks for the responses.  

garvinrick4: I followed your instructions but when I booted the flash drive grub wouldn't take the update-grub command.  So I just reinstalled the operating system but this time installed grub to sdb and not sdb1, as I did last time, and everything worked out.

I actually read this somewhere with regards to installing grub but I don't quite understand what difference it makes.  In the past my setup has been: Truecrypt encrypted Windows (sda1), /boot (sda2) and the encrypted lvm at sda3.  I've always installed grub, in such a setup, to sda2 without any problem.  This has to be done to avoid writing over the TC boot loader.  So why, when directing grub to the flash drive, does it have to be specified as sdb without the use of the partition number?

Thanks again.

---

