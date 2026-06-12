---
title: "Grub2 Loader issue when running &quot;update-grub&quot;"
date: 2010-05-16
forum: General Help
---

### Post by DarkPontiac on 2010-05-16
So I finally got Ubuntu 10.04 running on my fakeraid with 6 hard drives raid0.

What I did was not install the bootloader with the Ubuntu install but ran "grub-install /dev/mapper/raidname" manually and then update-grub.

System boots fine only if I modify the bootloader manually in /boot/grub/grub.cfg 

what happens is update grub creates this:

```
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set [insert uuid here]
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=[insert uuid here] ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
```

(I changed the uuid to the insert uuid here)

which doesn't work... What i did was change it to this:

```
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,0)'
	search --no-floppy --fs-uuid --set [insert uuid here]
	linux	/boot/vmlinuz-2.6.32-22-generic root=/dev/mapper/pdc_bgbdfajdb1 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
```

This actually boots the system perfectly, problem is everytime I do an update that invovles changing the bootloader (kernal updates or grub updates) it will break the bootloader by putting the uuid.

Is there anyway in making this work with out me having to modify this manually?

---

### Post by DarkPontiac on 2010-05-16
To update,

I went ahead and removed grub2 and install grub legacy and it now works when using update-grub and so far it boots 10.04 without a problem

---

