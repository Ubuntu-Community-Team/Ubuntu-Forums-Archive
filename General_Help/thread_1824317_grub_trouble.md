---
title: "grub trouble"
date: 2011-08-13
forum: General Help
---

### Post by djallalnamri on 2011-08-13
hello 
i am on dual boot ubuntu/winxp
according to gparted :
winxp's partition should be sdb1
while in grub-splash it is located as sda1
in fact sda1 is a FAT32 partition with no os installed on it
this is why i cannot boot with winxp
is it possible to edit grub and modify it ???
thanks in advance ...

---

### Post by drs305 on 2011-08-13
Are you using Wubi or do you have a separate Ubuntu installation on its own partition?

If you can't access Windows from the Grub menu, and the reason is that the address is incorrect: Highlight the Windows menuentry, press 'e' to edit it, and if it's using the 'chainloader' command just change the 'chainloader' address (from 0 to 1 or vice versa) then press CTRL-x to boot Windows (until we can fix things).

Please boot Ubuntu and download/extract/run the boot info script from the following site and post the contents of RESULTS.txt. That should show us what is happening with your boot files.
[http://bootinfosource.sorceforge.net]("http://bootinfosource.sorceforge.net")

---

### Post by djallalnamri on 2011-08-13
> **drs305 said:**
> Are you using Wubi or do you have a separate Ubuntu installation on its own partition?

If you can't access Windows from the Grub menu, and the reason is that the address is incorrect: Highlight the Windows menuentry, press 'e' to edit it, and if it's using the 'chainloader' command just change the 'chainloader' address (from 0 to 1 or vice versa) then press CTRL-x to boot Windows (until we can fix things).

Please boot Ubuntu and download/extract/run the boot info script from the following site and post the contents of RESULTS.txt. That should show us what is happening with your boot files.
[http://bootinfosource.sorceforge.net]("http://bootinfosource.sorceforge.net")

first ... thanks a lot for quick reply
i have 3 hdd: /dev/sda,/dev/sdb/and /dev/sdc/
i do not use wubi
i use gparted to partition hdd
i usually install windows before installing ubuntu as recommended 
i am going to follow your advice
thanks again

---

### Post by djallalnamri on 2011-08-13
i am awesome sorry as i forgot to mention that after having installed the 3rd hdd ... i have partitioned it in order to install windows 7 and ubuntu 11.04
after this i did suppress win 7 partition
but it still appears on grub splash :
[B][COLOR="Red"]### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod fat
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 8c3e-aa8a
	chainloader +1[/COLOR][/B]


[COLOR="Black"][/COLOR]

may be the correct entry should be :


[COLOR="Blue"]### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professionnel (on /dev/sda1)" {
	insmod fat
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 8c3e-aa8a
	drivemap -s (hd0) ${root}
	chainloader +1[/COLOR]


[COLOR="Black"][/COLOR]

thanks in advance

---

### Post by drs305 on 2011-08-13
> **djallalnamri said:**
> i am awesome sorry as i forgot to mention that after having installed the 3rd hdd ... i have partitioned it in order to install windows 7 and ubuntu 11.04
after this i did suppress win 7 partition
but it still appears on grub splash :

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod fat
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 8c3e-aa8a
	chainloader +1

may be the correct entry should be :

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professionnel (on /dev/sda1)" {
	insmod fat
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 8c3e-aa8a
	drivemap -s (hd0) ${root}
	chainloader +1



I'm a bit confused by your situation. You say you tried to 'suppress' Win7. Do you want to use it?

I'm not a Windows guy, so someone else will probably have to help you. But posting RESULTS.txt will really help analyze your situation.

As far as the menu entry, from the Grub 2 menu, press 'e' then cursor and remove the entire search line with the DEL key and try changing the value of "set root=(hd0,1)" to "set root=(hd1,1)" or "set root=(hd2,1)" and press CTRL-x to boot. These are just guesses until you post RESULTS.txt

Also, a minor point on the Ubuntu forums: using different fonts/colors is generally discouraged, although including the sections you posted within "QUOTE" tags would be appropriate. You can generate tags from the icons in the post's menu.

---

