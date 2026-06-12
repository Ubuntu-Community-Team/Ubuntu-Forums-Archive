---
title: "is anyone else having this problem?"
date: 2010-11-23
forum: General Help
---

### Post by brandenmikal on 2010-11-23
after updating to the latest kernel using the update manager; after installing or uninstalling you get a box saying "package failed"

how can this be fixed or can someone tell me what to do to prevent it from popping up?

below is the details within the popup dialog and a screenshot of what comes up after uninstalling a program. if anyone knows a code or anything let me know. it seems it has to do with the linux kernel image having some sort of error after updating earlier using the update manager.

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
(Reading database ... 201331 files and directories currently installed.)
Removing gmchess ...
Removing convert-pgn ...
Removing eleeye ...
Removing libeval0 ...
Processing triggers for man-db ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.UTF8.cache...
Processing triggers for desktop-file-utils ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for python-support ...
Setting up linux-image-2.6.35-23-generic (2.6.35-23.40) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-23-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic
Generating grub.cfg ...
/usr/sbin/grub-probe: error: cannot seek `/dev/sda'.
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-23-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.35-23-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.35-23-generic; however:
  Package linux-image-2.6.35-23-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.35.23.25); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
Errors were encountered while processing:
 linux-image-2.6.35-23-generic
 linux-image-generic
 linux-generic
Setting up linux-image-2.6.35-23-generic (2.6.35-23.40) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-23-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic
Generating grub.cfg ...
/usr/sbin/grub-probe: error: cannot seek `/dev/sda'.
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-23-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.35-23-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.35-23-generic; however:
  Package linux-image-2.6.35-23-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.35.23.25); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.35-23-generic
 linux-image-generic
 linux-generic


---

### Post by NightwishFan on 2010-11-24
This line is the killer:
```
/usr/sbin/grub-probe: error: cannot seek `/dev/sda'.
```

Is something wrong with your /dev/sda drive?

Also try this command:
```
sudo dpkg --force-all -P linux-image-2.6.35-23-generic
```

Then run:
```
sudo update-grub
```

Finally, try to install the kernel package again:
```
sudo apt-get update
```

---

### Post by brandenmikal on 2010-11-24
> **NightwishFan said:**
> This line is the killer:
```
/usr/sbin/grub-probe: error: cannot seek `/dev/sda'.
```

Is something wrong with your /dev/sda drive?

Also try this command:
```
sudo dpkg --force-all -P linux-image-2.6.35-23-generic
```

Then run:
```
sudo update-grub
```

Finally, try to install the kernel package again:
```
sudo apt-get update
```

i don't believe so but if none of the commands are helping; that says i may need to reinstall the OS or perhaps it affected the other partition with windows on it.

---

