---
title: "being offered partial upgrade on PP including linux kernel which wont install?"
date: 2012-04-26
forum: General Help
---

### Post by sdowney717 on 2012-04-26
What gives, any ideas?

---

### Post by codingman on 2012-04-26
Is this on 12.04 beta? Or on 11.10 or earlier? I'd like some more info on your problem.

---

### Post by cryptotheslow on 2012-04-26
The repositories are being absolutely hammered today due to the new release. It's also possible that the new release has not fully replicated to your particular repository.

I'd give it a few hours and check for updates again to see if it clears up.

---

### Post by sdowney717 on 2012-04-26
yes 12.04 beta which does update to the final release. OR should update, it always has in the past, so beta should now not mean anything.

---

### Post by sdowney717 on 2012-04-28
a few updates went threw today and still left with the same Linux kernel and gnome issue partial upgrade.

---

### Post by sdowney717 on 2012-04-28
ok, so I closed to gui update manager and opened terminal and then ran
'sudo apt-get dist-upgrade'
And it all went ok.
So it is sort of solved in a way, but who knows what an unfamiliar person will know what to do?

> ```
scott@scott-P5QC:~$ sudo apt-get dist-upgrade
[sudo] password for scott: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  gir1.2-gjs-1.0
The following NEW packages will be installed:
  gir1.2-gjsdbus-1.0 linux-headers-3.2.0-24 linux-headers-3.2.0-24-generic-pae
  linux-image-3.2.0-24-generic-pae
The following packages will be upgraded:
  gnome-shell gnome-shell-common linux-generic-pae linux-headers-generic-pae
  linux-image-generic-pae
5 upgraded, 4 newly installed, 1 to remove and 0 not upgraded.
Need to get 51.6 MB of archives.
After this operation, 180 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ precise/universe gnome-shell i386 3.4.1-0ubuntu2 [338 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ precise/universe gnome-shell-common all 3.4.1-0ubuntu2 [1,059 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ precise/universe gir1.2-gjsdbus-1.0 i386 1.32.0-1ubuntu1 [4,280 B]
Get:4 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main linux-image-3.2.0-24-generic-pae i386 3.2.0-24.37 [37.9 MB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main linux-generic-pae i386 3.2.0.24.26 [1,718 B]
Get:6 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main linux-image-generic-pae i386 3.2.0.24.26 [2,528 B]
Get:7 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main linux-headers-3.2.0-24 all 3.2.0-24.37 [11.4 MB]
Get:8 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main linux-headers-3.2.0-24-generic-pae i386 3.2.0-24.37 [943 kB]
Get:9 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main linux-headers-generic-pae i386 3.2.0.24.26 [2,528 B]
Fetched 51.6 MB in 26s (1,960 kB/s)                                            
(Reading database ... 387524 files and directories currently installed.)
Preparing to replace gnome-shell 3.4.0-0ubuntu3 (using .../gnome-shell_3.4.1-0ubuntu2_i386.deb) ...
Unpacking replacement gnome-shell ...
Preparing to replace gnome-shell-common 3.4.0-0ubuntu3 (using .../gnome-shell-common_3.4.1-0ubuntu2_all.deb) ...
Unpacking replacement gnome-shell-common ...
Processing triggers for libglib2.0-0 ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
(Reading database ... 387523 files and directories currently installed.)
Removing gir1.2-gjs-1.0 ...
Selecting previously unselected package gir1.2-gjsdbus-1.0.
(Reading database ... 387518 files and directories currently installed.)
Unpacking gir1.2-gjsdbus-1.0 (from .../gir1.2-gjsdbus-1.0_1.32.0-1ubuntu1_i386.deb) ...
Selecting previously unselected package linux-image-3.2.0-24-generic-pae.
Unpacking linux-image-3.2.0-24-generic-pae (from .../linux-image-3.2.0-24-generic-pae_3.2.0-24.37_i386.deb) ...
Done.
Preparing to replace linux-generic-pae 3.2.0.23.25 (using .../linux-generic-pae_3.2.0.24.26_i386.deb) ...
Unpacking replacement linux-generic-pae ...
Preparing to replace linux-image-generic-pae 3.2.0.23.25 (using .../linux-image-generic-pae_3.2.0.24.26_i386.deb) ...
Unpacking replacement linux-image-generic-pae ...
Selecting previously unselected package linux-headers-3.2.0-24.
Unpacking linux-headers-3.2.0-24 (from .../linux-headers-3.2.0-24_3.2.0-24.37_all.deb) ...
Selecting previously unselected package linux-headers-3.2.0-24-generic-pae.
Unpacking linux-headers-3.2.0-24-generic-pae (from .../linux-headers-3.2.0-24-generic-pae_3.2.0-24.37_i386.deb) ...
Preparing to replace linux-headers-generic-pae 3.2.0.23.25 (using .../linux-headers-generic-pae_3.2.0.24.26_i386.deb) ...
Unpacking replacement linux-headers-generic-pae ...
Setting up gnome-shell-common (3.4.1-0ubuntu2) ...
Setting up gir1.2-gjsdbus-1.0 (1.32.0-1ubuntu1) ...
Setting up gnome-shell (3.4.1-0ubuntu2) ...
Setting up linux-image-3.2.0-24-generic-pae (3.2.0-24.37) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-24-generic-pae /boot/vmlinuz-3.2.0-24-generic-pae
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-24-generic-pae /boot/vmlinuz-3.2.0-24-generic-pae
update-initramfs: Generating /boot/initrd.img-3.2.0-24-generic-pae
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-24-generic-pae /boot/vmlinuz-3.2.0-24-generic-pae
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-24-generic-pae /boot/vmlinuz-3.2.0-24-generic-pae
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-24-generic-pae /boot/vmlinuz-3.2.0-24-generic-pae
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-24-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-24-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-23-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-23-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-22-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-22-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-21-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-21-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-20-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-20-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-19-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-19-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-18-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-18-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-17-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-17-generic-pae
Found linux image: /boot/vmlinuz-3.0.0-16-generic-pae
Found initrd image: /boot/initrd.img-3.0.0-16-generic-pae
Found linux image: /boot/vmlinuz-2.6.38-12-generic-pae
Found initrd image: /boot/initrd.img-2.6.38-12-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda1
done
Setting up linux-image-generic-pae (3.2.0.24.26) ...
Setting up linux-generic-pae (3.2.0.24.26) ...
Setting up linux-headers-3.2.0-24 (3.2.0-24.37) ...
Setting up linux-headers-3.2.0-24-generic-pae (3.2.0-24.37) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.2.0-24-generic-pae /boot/vmlinuz-3.2.0-24-generic-pae
Setting up linux-headers-generic-pae (3.2.0.24.26) ...
scott@scott-P5QC:~$ 

```

---

### Post by xyzzyman on 2012-04-28
Open up a terminal and type

```
sudo apt-get update
```

Then

```
sudo apt-get dist-upgrade
```

And highlight-copy-paste what the response is from the second command. It'll tell us what if anything is holding it back.

---

### Post by xyzzyman on 2012-04-28
Ha! Great timing. The upgrade from gir1.2-gjs-1.0 to gir1.2-gjsdbus-1.0 was holding it up.

---

### Post by sdowney717 on 2012-04-28
Thanks and Yeah, I already just did that.

So why will that have to be done outside of the gui?
Think if you want to be 100% user friendly, then this type of thing needs to be done away with. It is ok for those with a brain and can think to figure out, but most people dont have a clue and would just say it is broken. For most people computers are not easy.

---

