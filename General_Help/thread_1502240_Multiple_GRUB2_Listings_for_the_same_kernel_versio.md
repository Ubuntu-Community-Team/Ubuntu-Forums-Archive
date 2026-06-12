---
title: "Multiple GRUB2 Listings for the same kernel version"
date: 2010-06-05
forum: General Help
---

### Post by jdholman on 2010-06-05
Hello:

I did a fresh 64-bit install of 10.04 workstation a few weeks ago, and my grub seems to "double up" the listings of my kernel versions.  I have removed the older versions hanging around on my system, but you can see in the list below, that I still get the listings more than once:

jim@jim-laptop:/etc/grub.d$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Ubuntu 10.04 LTS (10.04) on /dev/sda5
done

Why is /boot/vmlinuz-2.6.32-22-generic listed 2 times?

Any thoughts on this?

Thanks,

Jim

---

### Post by dragos240 on 2010-06-05
> **jdholman said:**
> Hello:

I did a fresh 64-bit install of 10.04 workstation a few weeks ago, and my grub seems to "double up" the listings of my kernel versions.  I have removed the older versions hanging around on my system, but you can see in the list below, that I still get the listings more than once:

jim@jim-laptop:/etc/grub.d$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Ubuntu 10.04 LTS (10.04) on /dev/sda5
done

Why is /boot/vmlinuz-2.6.32-22-generic listed 2 times?

Any thoughts on this?

Thanks,

Jim

I've had this happen a few times before. I'm not exactly sure why it does this, but it does. Feel free to delete the extras. No harm in it.

---

### Post by jdholman on 2010-06-05
Hi Drago:

From where do I delete them?  GRUB.CFG?  Looks ugly.

Jim

---

### Post by Leppie on 2010-06-05
could you post the output of the following command:
```
ls -al /boot
```

---

### Post by jdholman on 2010-06-05
Sure.  Here it is:

[FONT="Courier New"]jim@jim-laptop:~$ ls -al /boot
total 15156
drwxr-xr-x  3 root root    4096 2010-06-05 09:00 .
drwxr-xr-x 24 root root    4096 2010-06-05 09:00 ..
-rw-r--r--  1 root root  634929 2010-06-03 18:53 abi-2.6.32-22-generic
-rw-r--r--  1 root root  110365 2010-06-03 18:53 config-2.6.32-22-generic
drwxr-xr-x  3 root root    4096 2010-06-05 09:01 grub
-rw-r--r--  1 root root 8395044 2010-06-04 09:37 initrd.img-2.6.32-22-generic
-rw-r--r--  1 root root  160280 2010-03-23 05:40 memtest86+.bin
-rw-r--r--  1 root root 2152657 2010-06-03 18:53 System.map-2.6.32-22-generic
-rw-r--r--  1 root root    1336 2010-06-03 18:56 vmcoreinfo-2.6.32-22-generic
-rw-r--r--  1 root root 4037792 2010-06-03 18:53 vmlinuz-2.6.32-22-generic[/FONT]

---

### Post by dino99 on 2010-06-05
sudo grub-mkconfig
sudo update-grub

---

### Post by Leppie on 2010-06-05
could you post your grub.cfg as well?

---

### Post by jdholman on 2010-06-11
Hi Leppie,

Here is my GRUB.CFG (renamed grub.txt).  Updating GRUB finds multiple instances of the same kernel version for some reason.

I usually end up manually editing this file each time GRUB gets rebuilt to keep the boot menu smaller, but this is a pain.

Thanks,

Jim

---

### Post by Leppie on 2010-06-11
you've created a backup of your 10_linux script, but never removed the executable bit. this causes the kernels to be processed twice:
```
[COLOR="Red"]### BEGIN /etc/grub.d/10_linux.bak ###[/COLOR]
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 727227ff-2770-445d-bc1d-09a3e09147d5
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=727227ff-2770-445d-bc1d-09a3e09147d5 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 727227ff-2770-445d-bc1d-09a3e09147d5
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=727227ff-2770-445d-bc1d-09a3e09147d5 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
[COLOR="Red"]### END /etc/grub.d/10_linux.bak ###[/COLOR]
```
reset the executable bit:
```
sudo chmod a-x /etc/grub.d/10_linux.bak
```
and run update-grub again:
```
sudo update-grub
```

---

### Post by jdholman on 2010-06-11
Hi Leppie.

Thank you for your reply.  I did as you suggested and re-updated grub.  The BAK part of section 10 was removed, which is good.

The part that is still present is all of the Ubunto listings under section 30 (os-prober).  See attached.

I get 2.6.32-22 and 2.6.32-21 both in recovery mode and in "normal" mode.  All detected on /dev/sda5.  Why would the os proper find Ubuntu then it is already under section 10?  Could these be the 32-bit kernels from before I re-installed 10.04 64 bit?

Look at the attached screenshot.  Aren't these "pae" kernels (right panel)the old 32-bit ones?  Can I just delete all the "pae" files?  The left panel presumably is the 64-bit non "pae" kernels.  I think...

Anyway, I still have a ton of items in section 30 when I would only like Windows 7 to show up.

Thoughts?

Thanks,

Jim

---

### Post by Leppie on 2010-06-13
> **jdholman said:**
> I did as you suggested and re-updated grub.  The BAK part of section 10 was removed, which is good.

The part that is still present is all of the Ubunto listings under section 30 (os-prober).  See attached.
sorry, i hadn't noticed that there was a part under 30_os-prober as well.
it seems like your harddrive still has the old ubuntu root partition (on sda5).
your current root partition is:
```
UUID=727227ff-2770-445d-bc1d-09a3e09147d5
```but there's also the partition sda5 (which was never deleted or formatted before installing the x64 system):
```
UUID=21f9d030-a131-4b67-88c0-78fb5798e97e
```if you want to remove those kernel entries, just format the partition sda5 and run update-grub afterwards:
```
sudo update-grub
```> **jdholman said:**
> I get 2.6.32-22 and 2.6.32-21 both in recovery mode and in "normal" mode.  All detected on /dev/sda5.  Why would the os proper find Ubuntu then it is already under section 10?  Could these be the 32-bit kernels from before I re-installed 10.04 64 bit?
if you want to remove the recovery mode options from the menu, open the grub defaults file with a text editor:
```
gksudo gedit /etc/default/grub
```and uncomment the following line like this:
```
GRUB_DISABLE_LINUX_RECOVERY="true"
```then run update-grub to regenerate grub.cfg:
```
sudo update-grub
```> **jdholman said:**
>  Aren't these "pae" kernels (right panel)the old 32-bit ones?  Can I just delete all the "pae" files?  The left panel presumably is the 64-bit non "pae" kernels.  I think...
pae stand for Physical Address Extension, which makes it possible to have more than 4gb of total memory (RAM and Video memory) on your 32 bit system. for more info on pae, have a look at this page: [http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)

---

### Post by jdholman on 2010-06-14
Leppie,

You're a gentleperson and a scholar.  I somehow installed Lucid 64-bit without removing the 32-bit partition.  That pesky grub kept finding it.  If it didn't, I'd still have the 32-bit stuff out there.

Thanks again!

Jim

---

