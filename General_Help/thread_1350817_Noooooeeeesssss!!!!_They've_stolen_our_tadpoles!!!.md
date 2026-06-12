---
title: "Noooooeeeesssss!!!! They've stolen our tadpoles!!!"
date: 2009-12-09
forum: General Help
---

### Post by Draygera on 2009-12-09
Now a new problem!!!! :sad:

Setting up linux-image-2.6.31.7-candela (2.6.31.7-candela-10.00.Custom) ...

 Hmm. There is a symbolic link /lib/modules/2.6.31.7-candela/build
 However, I can not read it: No such file or directory
 Therefore, I am deleting /lib/modules/2.6.31.7-candela/build

Running depmod.
Finding valid ramdisk creators.
Using mkinitramfs-kpkg to build the ramdisk.
initrd.img(/boot/initrd.img-2.6.31.7-candela
) points to /boot/initrd.img-2.6.31.7-candela
 (/boot/initrd.img-2.6.31.7-candela) -- doing nothing at /var/lib/dpkg/info/linux-image-2.6.31.7-candela.postinst line 588.
vmlinuz(/boot/vmlinuz-2.6.31.7-candela
) points to /boot/vmlinuz-2.6.31.7-candela
 (/boot/vmlinuz-2.6.31.7-candela) -- doing nothing at /var/lib/dpkg/info/linux-image-2.6.31.7-candela.postinst line 588.
Running postinst hook script update-grub.
error: cannot open `/dev/sdc' while attempting to get disk size
error: cannot open `/dev/sdc' while attempting to get disk size
Generating grub.cfg ...
error: cannot open `/dev/sdc' while attempting to get disk size
error: cannot open `/dev/sdc' while attempting to get disk size
error: cannot open `/dev/sdc' while attempting to get disk size
error: cannot open `/dev/sdc' while attempting to get disk size
error: cannot open `/dev/sdc' while attempting to get disk size
Found linux image: /boot/vmlinuz-2.6.31.7-candela
Found initrd image: /boot/initrd.img-2.6.31.7-candela
error: cannot open `/dev/sdc' while attempting to get disk size
error: cannot open `/dev/sdc' while attempting to get disk size
error: cannot open `/dev/sdc' while attempting to get disk size
error: cannot open `/dev/sdc' while attempting to get disk size
error: cannot open `/dev/sdc' while attempting to get disk size
error: cannot open `/dev/sdc' while attempting to get disk size
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
error: cannot open `/dev/sdc' while attempting to get disk size
error: cannot open `/dev/sdc' while attempting to get disk size
error: cannot open `/dev/sdc' while attempting to get disk size
error: cannot open `/dev/sdc' while attempting to get disk size
error: cannot open `/dev/sdc' while attempting to get disk size
error: cannot open `/dev/sdc' while attempting to get disk size
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
error: cannot open `/dev/sdc' while attempting to get disk size
error: cannot open `/dev/sdc' while attempting to get disk size
error: cannot open `/dev/sdc' while attempting to get disk size
error: cannot open `/dev/sdc' while attempting to get disk size
error: cannot open `/dev/sdc' while attempting to get disk size
error: cannot open `/dev/sdc' while attempting to get disk size
Found memtest86+ image: /boot/memtest86+.bin
done
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms
run-parts: executing /etc/kernel/postinst.d/nvidia-common
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 20
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.31.7-candela.postinst line 1186.
dpkg: error processing linux-image-2.6.31.7-candela (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.31.7-candela
E: Sub-process /usr/bin/dpkg returned an error code (1)

When I tried to install the new kernel.

Can anyone help me with this problem? Please and thank you!!!

---

### Post by Draygera on 2009-12-10
Bump

---

### Post by livigagl on 2010-02-09
Probably you don't need help anymore but maybe someone else will find this information useful.
I received the error:
cannot open /dev/sdc while attempting to get disk size
giving the command:
```
update-grub
```and I solved this issue modifying the file /boot/grub/device.map as follows:
```
(hd0)   /dev/sda
(hd1)   /dev/sdb
#(hd2)  /dev/sdc

```I added a # to comment out the last line.

---

### Post by produnis on 2011-04-06
thanks livigagl,
you made my day!
:)

---

