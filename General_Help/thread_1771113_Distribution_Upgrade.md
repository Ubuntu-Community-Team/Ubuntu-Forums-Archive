---
title: "Distribution Upgrade"
date: 2011-05-30
forum: General Help
---

### Post by Scunnered on 2011-05-30
As usual I was notified that there was an update available via the Update Manager which I duly accepted.  I was then confronted with a popup which advised that there was a Distribution Upgrade and that it was to be a partial upgrade.

Finding that I would not go away I accepted the data finding that 9 packages were made available and 33 unused ones were to be deleted.

As this is my first experience of this is it something I need worry about and if so what should I do about it?

---

### Post by An Sanct on 2011-05-30
There is nothing to worry, but my advice to you would be to stay away from "partial" upgrades - unless you are 100% sure what you are doing.

At a partial upgrade you should know the packages, dependencies and all the other stuff, that killed my OS a few times :)

PS. are you using 10.04 as stated in your avatar??? because if so, you shouldn't get the distribution upgrade prompt - 10.04 = LTS, distribution upgrades for LTSs are LTS ... Please correct me anyone if I'm wrong!

---

### Post by plucky on 2011-05-30
I just got the same this morning on my X86_64 system as it has Wine installed and the Partial upgrade had to remove Wine 1.2 before it could install Wine 1.3.It also installed a new kernel.

```
sudo apt-get dist-upgrade
[sudo] password for peter: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED
  wine1.2
The following NEW packages will be installed
  linux-headers-2.6.32-32 linux-headers-2.6.32-32-generic
  linux-image-2.6.32-32-generic ttf-droid wine1.3 wine1.3-gecko
The following packages will be upgraded:
  linux-generic linux-headers-generic linux-image-generic linux-libc-dev
  ttf-symbol-replacement wine
6 upgraded, 6 newly installed, 1 to remove and 0 not upgraded.
Need to get 78.9MB of archives.
After this operation, 254MB of additional disk space will be used.
Do you want to continue [Y/n]? 
Get: 1 http://gb.archive.ubuntu.com/ubuntu/ lucid-updates/main linux-image-2.6.32-32-generic 2.6.32-32.62 [31.7MB]
Get: 2 http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ lucid/main wine1.3 1.3.19-0ubuntu1~lucid1~ppa1 [11.1MB]
Get: 3 http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ lucid/main wine 1.2.3-0ubuntu1~ppa1 [42.0kB]
Get: 4 http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ lucid/main ttf-symbol-replacement 1.2.3-0ubuntu1~ppa1 [58.0kB]
Get: 5 http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ lucid/main wine1.3-gecko 1.2.0-0ubuntu1~maverickppa1 [21.4MB]
Get: 6 http://gb.archive.ubuntu.com/ubuntu/ lucid-updates/main linux-generic 2.6.32.32.38 [4,534B]
Get: 7 http://gb.archive.ubuntu.com/ubuntu/ lucid-updates/main linux-image-generic 2.6.32.32.38 [4,540B]
Get: 8 http://gb.archive.ubuntu.com/ubuntu/ lucid-updates/main linux-headers-2.6.32-32 2.6.32-32.62 [10.1MB]
Get: 9 http://gb.archive.ubuntu.com/ubuntu/ lucid-updates/main linux-headers-2.6.32-32-generic 2.6.32-32.62 [806kB]
Get: 10 http://gb.archive.ubuntu.com/ubuntu/ lucid-updates/main linux-headers-generic 2.6.32.32.38 [4,532B]
Get: 11 http://gb.archive.ubuntu.com/ubuntu/ lucid-updates/main linux-libc-dev 2.6.32-32.62 [836kB]
Get: 12 http://gb.archive.ubuntu.com/ubuntu/ lucid/universe ttf-droid 1.00~b112+dfsg+1-0ubuntu1 [2,771kB]
Fetched 78.9MB in 2min 0s (652kB/s)                                            
Preconfiguring packages ...
dpkg: wine1.2: dependency problems, but removing anyway as you requested:
 wine depends on wine1.2.
(Reading database ... 189394 files and directories currently installed.)
Removing wine1.2 ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_GB.utf8.cache...
Processing triggers for desktop-file-utils ...
Processing triggers for man-db ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for python-support ...
Selecting previously deselected package wine1.3.
(Reading database ... 188260 files and directories currently installed.)
Unpacking wine1.3 (from .../wine1.3_1.3.19-0ubuntu1~lucid1~ppa1_amd64.deb) ...
Preparing to replace wine 1.2.2-1ubuntu1~lucid1 (using .../wine_1.2.3-0ubuntu1~ppa1_amd64.deb) ...
Unpacking replacement wine ...
Selecting previously deselected package linux-image-2.6.32-32-generic.
Unpacking linux-image-2.6.32-32-generic (from .../linux-image-2.6.32-32-generic_2.6.32-32.62_amd64.deb) ...
Done.
Preparing to replace ttf-symbol-replacement 1.2.2-1ubuntu1~lucid1 (using .../ttf-symbol-replacement_1.2.3-0ubuntu1~ppa1_all.deb) ...
Unpacking replacement ttf-symbol-replacement ...
Selecting previously deselected package wine1.3-gecko.
Unpacking wine1.3-gecko (from .../wine1.3-gecko_1.2.0-0ubuntu1~maverickppa1_amd64.deb) ...
Preparing to replace linux-generic 2.6.32.31.37 (using .../linux-generic_2.6.32.32.38_amd64.deb) ...
Unpacking replacement linux-generic ...
Preparing to replace linux-image-generic 2.6.32.31.37 (using .../linux-image-generic_2.6.32.32.38_amd64.deb) ...
Unpacking replacement linux-image-generic ...
Selecting previously deselected package linux-headers-2.6.32-32.
Unpacking linux-headers-2.6.32-32 (from .../linux-headers-2.6.32-32_2.6.32-32.62_all.deb) ...
Selecting previously deselected package linux-headers-2.6.32-32-generic.
Unpacking linux-headers-2.6.32-32-generic (from .../linux-headers-2.6.32-32-generic_2.6.32-32.62_amd64.deb) ...
Preparing to replace linux-headers-generic 2.6.32.31.37 (using .../linux-headers-generic_2.6.32.32.38_amd64.deb) ...
Unpacking replacement linux-headers-generic ...
Preparing to replace linux-libc-dev 2.6.32-31.61 (using .../linux-libc-dev_2.6.32-32.62_amd64.deb) ...
Unpacking replacement linux-libc-dev ...
Selecting previously deselected package ttf-droid.
Unpacking ttf-droid (from .../ttf-droid_1.00~b112+dfsg+1-0ubuntu1_all.deb) ...
Processing triggers for man-db ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_GB.utf8.cache...
Processing triggers for desktop-file-utils ...
Processing triggers for fontconfig ...
Processing triggers for python-support ...
Setting up wine1.3 (1.3.19-0ubuntu1~lucid1~ppa1) ...
procps stop/waiting
procps stop/waiting

Setting up wine (1.2.3-0ubuntu1~ppa1) ...
Setting up linux-image-2.6.32-32-generic (2.6.32-32.62) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-32-generic
Running postinst hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-32-generic
Found initrd image: /boot/initrd.img-2.6.32-32-generic
Found linux image: /boot/vmlinuz-2.6.32-31-generic
Found initrd image: /boot/initrd.img-2.6.32-31-generic
Found linux image: /boot/vmlinuz-2.6.32-30-generic
Found initrd image: /boot/initrd.img-2.6.32-30-generic
Found linux image: /boot/vmlinuz-2.6.32-29-generic
Found initrd image: /boot/initrd.img-2.6.32-29-generic
Found memtest86+ image: /boot/memtest86+.bin
done
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.32-32-generic /boot/vmlinuz-2.6.32-32-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.32-32-generic /boot/vmlinuz-2.6.32-32-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.32-32-generic /boot/vmlinuz-2.6.32-32-generic

Setting up ttf-symbol-replacement (1.2.3-0ubuntu1~ppa1) ...
Setting up wine1.3-gecko (1.2.0-0ubuntu1~maverickppa1) ...
Setting up linux-image-generic (2.6.32.32.38) ...
Setting up linux-generic (2.6.32.32.38) ...
Setting up linux-headers-2.6.32-32 (2.6.32-32.62) ...
Setting up linux-headers-2.6.32-32-generic (2.6.32-32.62) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 2.6.32-32-generic /boot/vmlinuz-2.6.32-32-generic
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common 2.6.32-32-generic /boot/vmlinuz-2.6.32-32-generic

Setting up linux-headers-generic (2.6.32.32.38) ...
Setting up linux-libc-dev (2.6.32-32.62) ...
Setting up ttf-droid (1.00~b112+dfsg+1-0ubuntu1) ...
No CIDSupplement specified for ZenHei, defaulting to 0.
No CIDSupplement specified for Dotum-Regular, defaulting to 0.
No CIDSupplement specified for Batang-Regular, defaulting to 0.
No CIDSupplement specified for Batang-Bold, defaulting to 0.
No CIDSupplement specified for DroidSansJapanese, defaulting to 0.
No CIDSupplement specified for DroidSansJapanese-JaH, defaulting to 0.
No CIDSupplement specified for Dotum-Bold, defaulting to 0.
No CIDSupplement specified for ZenHei-CNS, defaulting to 0.
Updating fontconfig cache for /usr/share/fonts/truetype/ttf-droid

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

```

This didn't happen on my 32-bit system,which doesn't have Wine installed.

I like to run "sudo apt-get dist-upgrade" from a terminal whenever "Update Manager" asks me to do a "Partial Upgrade" as it gives more information.

Good Luck

---

### Post by Scunnered on 2011-05-30
My thanks to you both for your replies.

From what you say I will just have to hope that things keep working as usual. I am using a 64 bit install but don't have wine so that is a bit strange.

Looks very much like a case of wish me luck

---

