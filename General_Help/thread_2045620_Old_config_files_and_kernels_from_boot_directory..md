---
title: "Old config files and kernels from /boot directory."
date: 2012-08-21
forum: General Help
---

### Post by kleenex on 2012-08-21
Hello, I have one, short question about kernel configuration, initrd files etc., which can be found in **/boot** directory (34 files at this time). "The Problem" is that with every kernel update, X/Ubuntu 12.04 does not delete old  kernels and config files, so there are more and more (I skipped files like e.g. [COLOR=Green]abi-3.2-0.x[/COLOR], [COLOR=Green]initrd-3.2-0.x[/COLOR] or [COLOR=Green]vmlinuz-3.2.0.x[/COLOR], because it is obvious, that these files are there).
```
[COLOR=Navy]$>[/COLOR] [COLOR=Navy][COLOR=SeaGreen]ls /boot |grep config[/COLOR]
[COLOR=Black]config-3.2.0-23-generic
config-3.2.0-24-generic
config-3.2.0-25-generic
config-3.2.0-26-generic
config-3.2.0-27-generic
config-3.2.0-29-generic[/COLOR]
[/COLOR]
[COLOR=Navy]$>[/COLOR] [COLOR=SeaGreen]dpkg -l |grep linux-image[/COLOR]
ii  linux-image-3.2.0-23-generic           3.2.0-23.36                             
ii  linux-image-3.2.0-24-generic           3.2.0-24.39                             
ii  linux-image-3.2.0-25-generic           3.2.0-25.40                             
ii  linux-image-3.2.0-26-generic           3.2.0-26.41                             
ii  linux-image-3.2.0-27-generic           3.2.0-27.43                             
ii  linux-image-3.2.0-29-generic           3.2.0-29.46                            
ii  linux-image-generic                    3.2.0.29.31                             

```Because I am using latest [COLOR=Green]3.2.0-29-generic[/COLOR] kernel version, it seems, that I can/should remove packages e.g. from 3.2.0-23 to 3.2.0-26. If so, what is the best method? Simply removing these files with **rm** utility? And what about Linux kernel image packages for these versions (7 at this time)? Should I remove them with **apt-get --purge remove** command?

Sorry for this type of question, but I thought that after kernel updates, Ubuntu will remove the old versions.

---

### Post by Doug S on 2012-08-21
You can just remove the package. Example of removing a few older kernels:```
doug@test-smy:~$ [COLOR=red]dpkg -l |grep image   [/COLOR][COLOR=black]<<< Which ones are installed?[/COLOR]
ii  libcupsimage2                           1.5.3-0ubuntu4                      Common UNIX Printing System(tm) - Raster image library
ii  libijs-0.35                             0.35-8                              IJS raster image transport protocol: shared library
rc  linux-image-3.2.0-20-generic-pae        3.2.0-20.32                         Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-23-generic-pae        3.2.0-23.36                         Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-24-generic-pae        3.2.0-24.39                         Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-26-generic-pae        3.2.0-26.41                         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-27-generic-pae        3.2.0-27.43                         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-29-generic-pae        3.2.0-29.46                         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.4.0-030400rc4-generic-pae 3.4.0-030400rc4.201204230908        Linux kernel image for version 3.4.0 on 32 bit x86 SMP
ii  linux-image-generic-pae                 3.2.0.29.31                         Generic Linux kernel image
doug@test-smy:~$ [COLOR=red]dpkg -l |grep header   [/COLOR][COLOR=black]<<< I could not recall if I installed the header files. It seems I did not.[/COLOR]
ii  libdw-dev                               0.152-1ubuntu3                      libdw1 development libraries and header files
ii  libelf-dev                              0.152-1ubuntu3                      libelf1 development libraries and header files
doug@test-smy:~$ [COLOR=red]ls -l /boot   [/COLOR][COLOR=black]<<< Does the boot directory agree? (sanity check)[/COLOR]
total 113045
-rw-r--r-- 1 root root   800195 Apr 10 19:17 abi-3.2.0-23-generic-pae
-rw-r--r-- 1 root root   800247 May 21 16:50 abi-3.2.0-24-generic-pae
-rw-r--r-- 1 root root   800498 Jun 14 10:46 abi-3.2.0-26-generic-pae
-rw-r--r-- 1 root root   800453 Jul  6 09:07 abi-3.2.0-27-generic-pae
-rw-r--r-- 1 root root   800453 Jul 27 11:35 abi-3.2.0-29-generic-pae
-rw-r--r-- 1 root root   147226 Apr 10 19:17 config-3.2.0-23-generic-pae
-rw-r--r-- 1 root root   147288 May 21 16:50 config-3.2.0-24-generic-pae
-rw-r--r-- 1 root root   147401 Jun 14 10:46 config-3.2.0-26-generic-pae
-rw-r--r-- 1 root root   147401 Jul  6 09:07 config-3.2.0-27-generic-pae
-rw-r--r-- 1 root root   147379 Jul 27 11:35 config-3.2.0-29-generic-pae
drwxr-xr-x 3 root root     5120 Aug 10 08:58 grub
-rw-r--r-- 1 root root 14687680 Apr 21 20:54 initrd.img-3.2.0-23-generic-pae
-rw-r--r-- 1 root root 14690487 Jul  3 17:24 initrd.img-3.2.0-24-generic-pae
-rw-r--r-- 1 root root 14705915 Jul  7 12:16 initrd.img-3.2.0-26-generic-pae
-rw-r--r-- 1 root root 14717634 Aug 10 08:43 initrd.img-3.2.0-27-generic-pae
-rw-r--r-- 1 root root 14722080 Aug 21 12:14 initrd.img-3.2.0-29-generic-pae
drwxr-xr-x 2 root root    12288 Apr 20 10:40 lost+found
-rw-r--r-- 1 root root   176764 Nov 27  2011 memtest86+.bin
-rw-r--r-- 1 root root   178944 Nov 27  2011 memtest86+_multiboot.bin
-rw------- 1 root root  2313006 Apr 10 19:17 System.map-3.2.0-23-generic-pae
-rw------- 1 root root  2313265 May 21 16:50 System.map-3.2.0-24-generic-pae
-rw------- 1 root root  2311100 Jun 14 10:46 System.map-3.2.0-26-generic-pae
-rw------- 1 root root  2311276 Jul  6 09:07 System.map-3.2.0-27-generic-pae
-rw------- 1 root root  2311324 Jul 27 11:35 System.map-3.2.0-29-generic-pae
-rw------- 1 root root  5015840 Apr 10 19:17 vmlinuz-3.2.0-23-generic-pae
-rw------- 1 root root  5017056 May 21 16:50 vmlinuz-3.2.0-24-generic-pae
-rw------- 1 root root  5009632 Jun 14 10:46 vmlinuz-3.2.0-26-generic-pae
-rw------- 1 root root  5010688 Jul  6 09:07 vmlinuz-3.2.0-27-generic-pae
-rw------- 1 root root  5010176 Jul 27 11:35 vmlinuz-3.2.0-29-generic-pae
doug@test-smy:~$ [COLOR=red]sudo dpkg -r linux-image-3.2.0-23-generic-pae   [/COLOR][COLOR=black]<<< Actually remove stuff[/COLOR]
[sudo] password for doug:
(Reading database ... 85782 files and directories currently installed.)
Removing linux-image-3.2.0-23-generic-pae ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-23-generic-pae /boot/vmlinuz-3.2.0-23-generic-pae
update-initramfs: Deleting /boot/initrd.img-3.2.0-23-generic-pae
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-23-generic-pae /boot/vmlinuz-3.2.0-23-generic-pae
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-29-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-29-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-27-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-27-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-26-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-26-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-24-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-24-generic-pae
Found memtest86+ image: /memtest86+.bin
done
doug@test-smy:~$ [COLOR=red]sudo dpkg -r linux-image-3.2.0-24-generic-pae[/COLOR]
(Reading database ... 81410 files and directories currently installed.)
Removing linux-image-3.2.0-24-generic-pae ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-24-generic-pae /boot/vmlinuz-3.2.0-24-generic-pae
update-initramfs: Deleting /boot/initrd.img-3.2.0-24-generic-pae
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-24-generic-pae /boot/vmlinuz-3.2.0-24-generic-pae
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-29-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-29-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-27-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-27-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-26-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-26-generic-pae
Found memtest86+ image: /memtest86+.bin
done
doug@test-smy:~$ [COLOR=red]sudo dpkg -r linux-image-3.2.0-26-generic-pae[/COLOR]
(Reading database ... 77039 files and directories currently installed.)
Removing linux-image-3.2.0-26-generic-pae ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-26-generic-pae /boot/vmlinuz-3.2.0-26-generic-pae
update-initramfs: Deleting /boot/initrd.img-3.2.0-26-generic-pae
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-26-generic-pae /boot/vmlinuz-3.2.0-26-generic-pae
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-29-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-29-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-27-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-27-generic-pae
Found memtest86+ image: /memtest86+.bin
done
doug@test-smy:~$ [COLOR=red]dpkg -l |grep image   [/COLOR][COLOR=black]<<< Check[/COLOR]
ii  libcupsimage2                           1.5.3-0ubuntu4                      Common UNIX Printing System(tm) - Raster image library
ii  libijs-0.35                             0.35-8                              IJS raster image transport protocol: shared library
rc  linux-image-3.2.0-20-generic-pae        3.2.0-20.32                         Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rc  linux-image-3.2.0-23-generic-pae        3.2.0-23.36                         Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rc  linux-image-3.2.0-24-generic-pae        3.2.0-24.39                         Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rc  linux-image-3.2.0-26-generic-pae        3.2.0-26.41                         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-27-generic-pae        3.2.0-27.43                         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-29-generic-pae        3.2.0-29.46                         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.4.0-030400rc4-generic-pae 3.4.0-030400rc4.201204230908        Linux kernel image for version 3.4.0 on 32 bit x86 SMP
ii  linux-image-generic-pae                 3.2.0.29.31                         Generic Linux kernel image
doug@test-smy:~$ [COLOR=red]ls -l /boot   [/COLOR][COLOR=black]<<< Check[/COLOR]
total 45463
-rw-r--r-- 1 root root   800453 Jul  6 09:07 abi-3.2.0-27-generic-pae
-rw-r--r-- 1 root root   800453 Jul 27 11:35 abi-3.2.0-29-generic-pae
-rw-r--r-- 1 root root   147401 Jul  6 09:07 config-3.2.0-27-generic-pae
-rw-r--r-- 1 root root   147379 Jul 27 11:35 config-3.2.0-29-generic-pae
drwxr-xr-x 3 root root     5120 Aug 21 13:58 grub
-rw-r--r-- 1 root root 14717634 Aug 10 08:43 initrd.img-3.2.0-27-generic-pae
-rw-r--r-- 1 root root 14722080 Aug 21 12:14 initrd.img-3.2.0-29-generic-pae
drwxr-xr-x 2 root root    12288 Apr 20 10:40 lost+found
-rw-r--r-- 1 root root   176764 Nov 27  2011 memtest86+.bin
-rw-r--r-- 1 root root   178944 Nov 27  2011 memtest86+_multiboot.bin
-rw------- 1 root root  2311276 Jul  6 09:07 System.map-3.2.0-27-generic-pae
-rw------- 1 root root  2311324 Jul 27 11:35 System.map-3.2.0-29-generic-pae
-rw------- 1 root root  5010688 Jul  6 09:07 vmlinuz-3.2.0-27-generic-pae
-rw------- 1 root root  5010176 Jul 27 11:35 vmlinuz-3.2.0-29-generic-pae
doug@test-smy:~$

```
There are some other suggestions here: [http://ubuntuforums.org/showthread.php?t=2045573](http://ubuntuforums.org/showthread.php?t=2045573)

---

### Post by kleenex on 2012-08-22
Hi **Doug S**. Thanks for the reply and example. I see that You used **dpkg** tool to remove kernel packages, but only with **-r** option, which is responsible for remove everything except conffiles. **-P** or  **--purge ** removes  everything,  including  conffiles, so why You have not used this option? I see that, in your example, after removing kernel packages (with only **-r** option)  there is no configuration files in the **/boot** directory for these packages, which You removed. Is it normal?

---

### Post by Statia on 2012-08-22
I found this guide helpful:

[http://tuxtweaks.com/2009/12/remove-old-kernels-in-ubuntu/](http://tuxtweaks.com/2009/12/remove-old-kernels-in-ubuntu/)

---

### Post by Doug S on 2012-08-22
Hi Kleenex,
I don't have any good reason for why I use the -r option instead of the -P. But yes, I always found it cleaned up /boot properly anyhow.

---

### Post by kleenex on 2012-08-23
Hi **Stati**.               Many thanks for the link, which assured me that removing older kernels is practically harmless. **Doug S **used [COLOR=SeaGreen]dpkg[/COLOR] utility, **Linerd **[COLOR=SeaGreen]aptitude[/COLOR], so I will use [COLOR=SeaGreen]apt-get[/COLOR] with **--purge** flag, because I am using [COLOR=SeaGreen]apt[/COLOR] for a long time. Thank You both for your help.

I found another interesting possibility to remove old kernels. It's one line with [COLOR=SeaGreen]apt-get[/COLOR] (source: _[COLOR=RoyalBlue][One-Liner to Purge Old Kernels]("http://charlesa.net/scripts/linux/purgekernel.php")[/COLOR]_); ```
[COLOR=Blue]>#[/COLOR] apt-get purge $(dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | head -n -1)
```As I said before I used [COLOR=SeaGreen]apt[/COLOR] utility with **--purge** flag.[COLOR=Blue] [COLOR=Black]Everything seems to be ok, but I am curious if computer will run again[COLOR=Black]?[/COLOR][/COLOR] [COLOR=Black]Oh, one more thing. [/COLOR][/COLOR]Sometimes I use VirtualBox. During remove [COLOR=Blue][COLOR=SeaGreen]linux-image-3.2.0-25[/COLOR] [COLOR=Black]kernel[/COLOR][COLOR=Black], I saw[/COLOR] [COLOR=Black]something interesting; [/COLOR][/COLOR]```
[COLOR=Blue]>#[/COLOR] apt-get --purge remove linux-image-3.2.0-25-generic
[COLOR=Blue][COLOR=Black](...)
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.2.0-25-generic /boot/vmlinuz-3.2.0-25-generic
dkms: removing: virtualbox 4.1.12 (3.2.0-25-generic) (i686)

-------- Uninstall Beginning --------
Module:  virtualbox
Version: 4.1.12
Kernel:  3.2.0-25-generic (i686)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

vboxdrv.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-25-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

**--->>>** [COLOR=Blue]Below are similar info about[/COLOR] [COLOR=SeaGreen]vboxpci.ko[/COLOR], [COLOR=SeaGreen]vboxnetflt.ko[/COLOR] [COLOR=Blue]modules etc.[/COLOR][/COLOR][/COLOR]
```[COLOR=Blue][COLOR=Black] VirtualBox seems to run correctly. [/COLOR][/COLOR]Is this normal? This message [COLOR=Blue][COLOR=Black]appeared only[/COLOR] [/COLOR]during removing one kernel.

**[COLOR=Red]>>>[/COLOR]** OK, computer run normally and **/boot** directory does not contain that many files as before, but what about these VirtualBox modules and info about it during removing one of the kernels? **[COLOR=Red]<<<[/COLOR]**

---

