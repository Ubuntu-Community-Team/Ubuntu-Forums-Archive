---
title: "How to remove unnecessary entries in the grub boo menu ?"
date: 2010-10-30
forum: General Help
---

### Post by mhmdrizmi on 2010-10-30
Hi,

I've got a dual boot PC with windows 7 & Ubuntu. I had installed Ubuntu 10.04 & recently upgraded it to 10.10. Now I have these entries in the boot menu.

Ubuntu with linux 2.6.35-22-generic
Ubuntu with linux 2.6.35-22-generic (recovery mode)
Ubuntu with linux 2.6.32-21-generic
Ubuntu with linux 2.6.32-21-generic (recovery mode)
Memory test (memtest 86+)
Memory test (memtest 86+, serial console 115200)
Windows 7 (loader) (on/dev/sda1)

First & second entries listed above don't work. How can I remove them safely ? Please help.  :(

---

### Post by Rubi1200 on 2010-10-30
Hi and welcome to the forums :-)

Do you want to keep 10.10?

If you get rid of the first 2 entries that will not allow you to boot 10.10

Do you mean the third and fourth entries (10.04) perhaps?

---

### Post by mhmdrizmi on 2010-10-31
Well Rubi1200, I definitely want to keep 10.10. But the problem is that the first 2 entries don't work. Third & 4th entries work. As I've mentioned earlier I recently upgraded 10.04 to 10.10. Using the 3rd & 4th entries I can access Ubuntu 10.10. So what should I do ?

---

### Post by Omnomnom on 2010-10-31
I would also like to know how to do this, but mine goes

Ubuntu Loader
Other ubuntu thing memtest number 1
Other ubuntu thing memtest number 2
Vista (actually recovery thing)
Vista Recovery Environment (Actually Vista)

Yeah... I just want to rename Vista Recovery to Windows Vista and vice versa...

---

### Post by Quackers on 2010-10-31
Have a look here

[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

---

### Post by Omnomnom on 2010-10-31
Meh, I don't like the looks of that :P. Never liked changing system/boot menu/anything that makes my computer go vroom configs. I'll just ignore it.

---

### Post by Quackers on 2010-10-31
It is a bit involved :-) And has its dangers - but I made backups first, which is good practice. A safety net is usually a good thing :-)

---

### Post by Rubi1200 on 2010-10-31
> **mhmdrizmi said:**
> Well Rubi1200, I definitely want to keep 10.10. But the problem is that the first 2 entries don't work. Third & 4th entries work. As I've mentioned earlier I recently upgraded 10.04 to 10.10. Using the 3rd & 4th entries I can access Ubuntu 10.10. So what should I do ?
If that is the case, then it seems there was a problem with the upgrade.

I would boot into Ubuntu using the third entry and run this command:

```
sudo dpkg --configure -a
```

Post back if it reports errors.

You can also try ```
sudo update-grub
``` and see if that changes anything because it seems, sometimes, that GRUB is not updated even though it should have happened automatically.

Please also post the output from the following commands (run separately)

```
sudo blkid
```

```
cat /etc/fstab
```

Thanks.

---

### Post by mhmdrizmi on 2010-11-01
Where should I run these commands? I'm new to Ubuntu. So could you please describe the steps ?

---

### Post by Quackers on 2010-11-01
In a terminal. That's Applications menu > Accessories > Terminal. Enter one command at a time.

---

### Post by mhmdrizmi on 2010-11-02
Thanks.
Here's what happened when I run these commands,

sudo dpkg --configure -a      
nothing happens

sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done

sudo blkid
/dev/sda1: LABEL="Windows" UUID="2E7479F47479BF61" TYPE="ntfs" 
/dev/sda5: LABEL="Rinosh" UUID="18BC48EEBC48C848" TYPE="ntfs" 
/dev/sda6: LABEL="Rizmi" UUID="0EFC285DFC284177" TYPE="ntfs" 
/dev/sda7: UUID="96953d36-29e7-4f7b-9bc5-89f84e0531ef" TYPE="ext4" 

cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
#Entry for /dev/sda7 :
UUID=96953d36-29e7-4f7b-9bc5-89f84e0531ef	/	ext4	errors=remount-ro	0	1
#Entry for /dev/sda5 :
UUID=18BC48EEBC48C848	/media/Rinosh	ntfs-3g	defaults,locale=en_US.utf8	00
#Entry for /dev/sda6 :
UUID=0EFC285DFC284177	/media/Rizmi	ntfs-3g	defaults,nosuid,nodev,locale=en_US.utf8	0	0
#Entry for /dev/sda1 :
UUID=2E7479F47479BF61	/media/Windows	ntfs-3g	defaults,locale=en_US.utf8	00
/dev/fd0	/media/floppy0	auto	rw,user,noauto,exec,utf8	0	0

---

### Post by mhmdrizmi on 2010-11-04
Guys I need help !!!!!!!

---

### Post by mhmdrizmi on 2010-11-13
Problem solved. I installed Ubuntu Tweak & cleaned the kernels, the unnecessary entries are removed.

---

