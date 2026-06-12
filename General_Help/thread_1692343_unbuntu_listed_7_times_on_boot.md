---
title: "unbuntu listed 7 times on boot"
date: 2011-02-21
forum: General Help
---

### Post by kev66 on 2011-02-21
can anyone tell me why unbuntu is listed 7 times on my boot menu?(14inc recovery mode

also listed are 
memory test
bell partician
win xp

unbuntu is listed with a number next to it going from 21 at the end to 28??

new to linux
not sure whats going on or what i can do about it :confused:

---

### Post by Quackers on 2011-02-21
Because you've got 7 different (updated) kernels installed.
If you go to System > Admin > Synaptic package manager and in the search box enter the first few digits of the kernel number (like 2.6.35 for instance) and in the main window of Synaptic all the currently installed kernels will appear listed.
It is advised to keep the current kernel (highest number) and one previous kernel (for recovery purposes) but the others can be deleted.
Being careful to avoid the last two, right-click on the other entries with a green box next to them, and select "mark for complete removal". There will be at least 2 entries for each kernel (maybe 3). When you're sure you've got them all click on the green tick in the toolbar to apply the change, then confirm and watch it run :-)
After it has run open up a terminal (Applications > Accessories > terminal) and run ```
sudo update-grub
```
Your new grub menu will be reduced in size.

---

### Post by wiggly81 on 2011-02-21
if i recall (i dont use dual boot so never really see grub) its a new entry for each kernal so when ubuntu updater updates the kernal it leave the old version so i think its a choice on boot.
you can easly edit the boot manager thou..

sudo gedit /boot/grub/grub.cfg
use a '#' to comment out all lines you dont want 

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 5de73c7d-2472-4ca0-9f24-c6d475d78d9e
	linux	/boot/vmlinuz-2.6.35-27-generic root=UUID=5de73c7d-2472-4ca0-9f24-c6d475d78d9e ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-27-generic
}
#menuentry 'Ubuntu, with Linux 2.6.35-27-generic (recovery mode)' #--class ubuntu --class gnu-linux --class gnu --class os {
#	recordfail
#	insmod part_msdos
#	insmod ext2
#	set root='(hd0,msdos1)'
#	search --no-floppy --fs-uuid --set 5de73c7d-2472-4ca0-9f24-c6d475d78d9e
#	echo	'Loading Linux 2.6.35-27-generic ...'
#	linux	/boot/vmlinuz-2.6.35-27-generic #root=UUID=5de73c7d-2472-4ca0-9f24-c6d475d78d9e ro single 
#	echo	'Loading initial ramdisk ...'
#	initrd	/boot/initrd.img-2.6.35-27-generic
#}

Somthing like this, alough i dont suggest you comment out recovery mode.


my post was too slow and was the only way i knew how to do it but i would say Quackers post is prolly much easier

---

### Post by seawolf167 on 2011-02-21
See [here ]("http://www.howtogeek.com/howto/ubuntu/clean-up-ubuntu-grub-boot-menu-after-upgrades/")for how to remove old menu entries. 

*I copied the first poster's comment and pasted below his instructions to only show 1 entry without deleting old entries.*

```
The easier way to keep only newest lines is to open the menu.lst (gksu  gedit /boot/grub/menu.lst), find “#howmany=all” and change it to  “#howmany=1&#8243;. Then run “sudo update-grub” to update changes. Next time,  only newest kernel lines will be shown.
```

---

### Post by Quackers on 2011-02-21
> **seawolf167 said:**
> See [here ]("http://www.howtogeek.com/howto/ubuntu/clean-up-ubuntu-grub-boot-menu-after-upgrades/")for how to remove old menu entries. 

*I copied the first poster's comment and pasted below his instructions to only show 1 entry without deleting old entries.*

```
The easier way to keep only newest lines is to open the menu.lst (gksu  gedit /boot/grub/menu.lst), find “#howmany=all” and change it to  “#howmany=1&#8243;. Then run “sudo update-grub” to update changes. Next time,  only newest kernel lines will be shown.
```

That will only work with grub legacy. If the OP has a later version of Ubuntu it is likely that grub2 will be in use.

---

### Post by kev66 on 2011-02-21
thanks for your help guys, should be able to get it sorted with the advice given:)

---

