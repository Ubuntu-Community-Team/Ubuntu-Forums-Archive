---
title: "Problem with Muon package manager"
date: 2011-10-27
forum: General Help
---

### Post by Alan.Brown on 2011-10-27
The computer froze while the package manager was being used a couple of days ago.   Now I can not do any updates because the system says another package manager is already in use.

I have tried rebooting several times.  I have looked in _**top**_ but cannot see anything to kill.   I need to stop the package manager from starting up at start time and blocking any further updates.   I have tried running in recovery mode.   Nothing helps.

Any Suggestions??

TIA

Alan.

---

### Post by dniMretsaM on 2011-10-27
Try running this in terminal:
```
sudo dpkg --configure -a
```

---

### Post by Alan.Brown on 2011-10-27
That worked OK - problem solved

Thank you

Alan

---

### Post by Alan.Brown on 2012-01-24
The same problem has occurred as in my first posting 3 months ago.

I have followed the instruction given above, rebooted, but the same problem keeps occurring.

TIA

Alan

---

### Post by CayleyGraph on 2013-01-19
Hello, all.

I am having the same problem as listed above.

When I run "sudo dpkg --configure -a" as instructed, I get a few messages and then the process just hangs, apparently doing nothing:
```
Setting up linux-image-3.2.0-36-generic (3.2.0-36.57) ...                                                                                                                                                                                    
Running depmod.                                                                                                                                                                                                                              
update-initramfs: deferring update (hook will be called later)                                                                                                                                                                               
Examining /etc/kernel/postinst.d.                                                                                                                                                                                                            
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-36-generic /boot/vmlinuz-3.2.0-36-generic                                                                                                                                             
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-36-generic /boot/vmlinuz-3.2.0-36-generic                                                                                                                                  
update-initramfs: Generating /boot/initrd.img-3.2.0-36-generic                                                                                                                                                                               
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-36-generic /boot/vmlinuz-3.2.0-36-generic                                                                                                                                         
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-36-generic /boot/vmlinuz-3.2.0-36-generic                                                                                                                                  
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-36-generic /boot/vmlinuz-3.2.0-36-generic                                                                                                                                   
Generating grub.cfg ...                                                                                                                                                                                                                      
Found linux image: /boot/vmlinuz-3.2.0-36-generic                                                                                                                                                                                            
Found initrd image: /boot/initrd.img-3.2.0-36-generic                                                                                                                                                                                        
Found linux image: /boot/vmlinuz-3.2.0-35-generic                                                                                                                                                                                            
Found initrd image: /boot/initrd.img-3.2.0-35-generic                                                                                                                                                                                        
Found linux image: /boot/vmlinuz-3.2.0-34-generic                                                                                                                                                                                            
Found initrd image: /boot/initrd.img-3.2.0-34-generic                                                                                                                                                                                        
Found linux image: /boot/vmlinuz-3.2.0-33-generic
Found initrd image: /boot/initrd.img-3.2.0-33-generic
Found linux image: /boot/vmlinuz-3.2.0-32-generic
Found initrd image: /boot/initrd.img-3.2.0-32-generic
Found linux image: /boot/vmlinuz-3.2.0-31-generic
Found initrd image: /boot/initrd.img-3.2.0-31-generic
Found linux image: /boot/vmlinuz-3.2.0-30-generic
Found initrd image: /boot/initrd.img-3.2.0-30-generic
Found linux image: /boot/vmlinuz-3.2.0-29-generic
Found initrd image: /boot/initrd.img-3.2.0-29-generic
Found linux image: /boot/vmlinuz-3.2.0-27-generic
Found initrd image: /boot/initrd.img-3.2.0-27-generic
Found linux image: /boot/vmlinuz-3.2.0-26-generic
Found initrd image: /boot/initrd.img-3.2.0-26-generic
Found linux image: /boot/vmlinuz-3.2.0-23-generic
Found initrd image: /boot/initrd.img-3.2.0-23-generic
Found memtest86+ image: /boot/memtest86+.bin
```After that, it's just... nothing for as long as I let it sit. It doesn't crash my computer or eat up a lot of resources or anything; it just doesn't display any additional information or error messages either.

I've checked other forums, one of which suggested running "sudo apt-get upgrade" instead, but that leads to exactly the same problem: After it installs the upgrade it found, the process sets up the Linux image and runs depmod, and everything afterwards in exactly the same as in the previously quoted output.

If anyone can give me advice, I would appreciate it. Thank you for your time.

---

### Post by SeijiSensei on 2013-01-19
Do you have a separate /boot partition?  Perhaps you have run out of space.  Try deleting all the older kernels except -35.  You may have to boot from an installation CD or USB device.  Then open a terminal and mount the boot partition like this:

```
sudo mount /dev/XXXX /mnt
```

replacing XXXX with the appropriate partition name like sda1.

Now run

```
cd /mnt
sudo rm -f *-2*
sudo rm -f *-3[01234]*

```

That will remove everything from -20 through -34.

---

### Post by CayleyGraph on 2013-01-19
> **SeijiSensei said:**
> Do you have a separate /boot partition?  Perhaps you have run out of space.  Try deleting all the older kernels except -35.  You may have to boot from an installation CD or USB device.  Then open a terminal and mount the boot partition like this:

```
sudo mount /dev/XXXX /mnt
```

replacing XXXX with the appropriate partition name like sda1.

Now run

```
cd /mnt
sudo rm -f *-2*
sudo rm -f *-3[01234]*

```

That will remove everything from -20 through -34.Thank you for the advice.

I checked my boot partition (which is, indeed, a separate partition) and it looked to me like it still had a lot of space on it. I deleted the leftover kernel images, etc. anyway and tried running "sudo dpkg --configure -a" again. Sadly, I get much the same result, except of course there aren't as many kernel images cluttering up the place:```
$ sudo dpkg --configure -a
Setting up linux-image-3.2.0-36-generic (3.2.0-36.57) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-36-generic /boot/vmlinuz-3.2.0-36-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-36-generic /boot/vmlinuz-3.2.0-36-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-36-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-36-generic /boot/vmlinuz-3.2.0-36-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-36-generic /boot/vmlinuz-3.2.0-36-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-36-generic /boot/vmlinuz-3.2.0-36-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-36-generic
Found initrd image: /boot/initrd.img-3.2.0-36-generic
Found memtest86+ image: /boot/memtest86+.bin
```If you (or anyone else) have additional ideas, they will be much appreciated.

---

