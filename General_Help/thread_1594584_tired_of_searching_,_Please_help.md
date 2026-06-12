---
title: "tired of searching , Please help ?"
date: 2010-10-12
forum: General Help
---

### Post by binarylife on 2010-10-12
Package operation failed!

> installArchives() failed: (Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 128641 files and directories currently installed.)
Preparing to replace linux-image-2.6.35-22-generic 2.6.35-22.33 (using .../linux-image-2.6.35-22-generic_2.6.35-22.34_i386.deb) ...
Done.
Unpacking replacement linux-image-2.6.35-22-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
Preparing to replace linux-headers-2.6.35-22 2.6.35-22.33 (using .../linux-headers-2.6.35-22_2.6.35-22.34_all.deb) ...
Unpacking replacement linux-headers-2.6.35-22 ...
Preparing to replace linux-headers-2.6.35-22-generic 2.6.35-22.33 (using .../linux-headers-2.6.35-22-generic_2.6.35-22.34_i386.deb) ...
Unpacking replacement linux-headers-2.6.35-22-generic ...
Preparing to replace linux-libc-dev 2.6.35-1022.33 (using .../linux-libc-dev_2.6.35-1022.34_i386.deb) ...
Unpacking replacement linux-libc-dev ...
Setting up firmware-b43-installer (4.150.10.5-4) ...
Not supported low-power chip with PCI id 14e4:4315!
Aborting.
dpkg: error processing firmware-b43-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up linux-image-2.6.35-22-generic (2.6.35-22.34) ...
No apport report written because MaxReports is reached already
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-22-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.35-22.33 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.35-22.33 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
 * dkms: running auto installation service for kernel 2.6.35-22-generic        
 *       bcmwl (5.60.48.36+bdcom)...        
[ OK ]
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done
Setting up linux-headers-2.6.35-22 (2.6.35-22.34) ...
Setting up linux-headers-2.6.35-22-generic (2.6.35-22.34) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
 * dkms: running auto installation service for kernel 2.6.35-22-generic        
 *       bcmwl (5.60.48.36+bdcom)...        
[ OK ]
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
Setting up linux-libc-dev (2.6.35-1022.34) ...
Errors were encountered while processing:
 firmware-b43-installer
Setting up firmware-b43-installer (4.150.10.5-4) ...
Not supported low-power chip with PCI id 14e4:4315!
Aborting.
dpkg: error processing firmware-b43-installer (--configure):
 subprocess installed post-installation script returned error exit status 1


How can i solve it without affecting the wireless please ? it was working fine with the beta !

---

### Post by binarylife on 2010-10-12
and this error while updating : 

W: GPG error: [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) maverick-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

---

### Post by 3Miro on 2010-10-12
In a situation like that, I would find a wired connection for my laptop, uninstall the driver and then install it again (or uninstall, update, reinstall).

---

### Post by binarylife on 2010-10-12
> **3Miro said:**
> In a situation like that, I would find a wired connection for my laptop, uninstall the driver and then install it again (or uninstall, update, reinstall).

I tried ! :(

---

### Post by scaine on 2010-10-12
I see the error complains about b43 firmware.  One quick search later...

[https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/655111](https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/655111)

From that, it looks like you might be fixed in a few hours, but only if you pop into Synaptic and enable "Proposed Updates" (from Settings/Repositories, then click the "Updates" tab to enable "Proposed Updates".

Fingers crossed.

---

### Post by binarylife on 2010-10-12
> **scaine said:**
> I see the error complains about b43 firmware.  One quick search later...

[https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/655111](https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/655111)

From that, it looks like you might be fixed in a few hours, but only if you pop into Synaptic and enable "Proposed Updates" (from Settings/Repositories, then click the "Updates" tab to enable "Proposed Updates".

Fingers crossed.

I did this . and it gave me this msg :

W: GPG error: [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) maverick-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

so it will be fixed soon as u said ?? 
thanks a lot

---

### Post by scaine on 2010-10-12
Looks like you've got a local mirror selected for your updates.  Might be worth setting this to the main server :

Start Synaptic, go to menu Settings/Respositories, then change "Download From" box to "Main Server".

Hit "reload" on your synaptic, then "Mark All Upgrades", then finally "Apply".

Worth a shot.  As for will it be fixed?  I have no idea, but the implication from the bug report is that this will fix it...

---

### Post by binarylife on 2010-10-12
> **scaine said:**
> Looks like you've got a local mirror selected for your updates.  Might be worth setting this to the main server :

Start Synaptic, go to menu Settings/Respositories, then change "Download From" box to "Main Server".

Hit "reload" on your synaptic, then "Mark All Upgrades", then finally "Apply".

Worth a shot.  As for will it be fixed?  I have no idea, but the implication from the bug report is that this will fix it...

i tried and i did it .. but nothing happens the same problem

---

### Post by otoris on 2010-10-12
I'm getting the exact same messages binarylife is getting.

I also tried switching to "Main Server" and it gives me the same error.

---

### Post by binarylife on 2010-10-12
> **otoris said:**
> I'm getting the exact same messages binarylife is getting.

I also tried switching to "Main Server" and it gives me the same error.

I think we should just wait for an update that will fix this bug ...and I believe it will be fixed soon ! 
but if there is anyone also having this problem and fixed it ... please help ??

---

### Post by binarylife on 2010-10-12
Dear otoris  , It worked finally : ) 
I did a normal restart , then clicked on additional drivers .. and deactivated the two drivers ...then activated them after that ,and it should work fine ..

---

### Post by otoris on 2010-10-13
That is awesome man! Thanks! ^^

---

