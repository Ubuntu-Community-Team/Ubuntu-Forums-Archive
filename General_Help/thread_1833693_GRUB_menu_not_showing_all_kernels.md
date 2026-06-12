---
title: "GRUB menu not showing all kernels"
date: 2011-08-26
forum: General Help
---

### Post by cinkler on 2011-08-26
Hi,

I am running 64-bit Ubuntu - it was 10.04 and updated twice to 11.04

some time back I had corrupted apt repository, and after doing various stuff to it, I succeeded in uninstalling ALL kernels.

I managed to fix it partially by booting from CD, sourcing from HDD and reinstalling kernel.

What happened, though, is following:

1. GRUB Start menu is showing as generic Debian and not ubuntu. It shows just 'repair' kernel entries and newly installed kernels (through apt-get) are not shown in the menu.

2. 'repair' kernels are working as such - so they don't boot all the way - they boot in the menu that shows boot options and when I choos 'resume normal boot' it boots to command prompt - so they don't boot into X.

3. Maybe not related, but command prompt colours are weird.

4. When I start X-Windows, it boots into empty screen - I need to start panel manually. 

5. I can switch between virtual desktops, but Alt-Tab doesn't work.

Any ideas?

boris

---

### Post by Enigmapond on 2011-08-26
Try:

```
sudo update-grub
```

---

### Post by cinkler on 2011-08-26
I think that I tried it already, however, will do it again right now and post result.

---

### Post by cinkler on 2011-08-26
here is what happened:

Generating grub.cfg ...
Found background image: /usr/share/images/desktop-base/desktop-grub.png
Found linux image: /boot/vmlinuz-2.6.38-11-generic
Found initrd image: /boot/initrd.img-2.6.38-11-generic
Found linux image: /boot/vmlinuz-2.6.38-10-generic
Found initrd image: /boot/initrd.img-2.6.38-10-generic
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found linux image: /boot/vmlinuz-2.6.35-28-generic
Found initrd image: /boot/initrd.img-2.6.35-28-generic
Found linux image: /boot/vmlinuz-2.6.35-27-generic
Found initrd image: /boot/initrd.img-2.6.35-27-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda2
error: syntax error.
error: Incorrect command.
error: syntax error.
error: line no: 110
[COLOR="Red"]Syntax errors are detected in generated GRUB config file.[/COLOR]
Ensure that there are no errors in /etc/default/grub
and /etc/grub.d/* files or please file a bug report with
/boot/grub/grub.cfg.new file attached.
done

---

### Post by cinkler on 2011-08-26
This is line 110:

[FONT="Courier New"]	linux	/boot/vmlinuz-2.6.38-11-generic root=UUID=acea25d1-d19e-4852-bd8e-4d15285dc2c7 ro   quiet splash nomodeset video=uvesafb:mode_option=>>1400x1050-24<<,mtrr=3,scroll=ywrap vt.handoff=7[/FONT]

I think that it was me who was playing with custom video mode.

---

### Post by Enigmapond on 2011-08-26
Is there any reason why you are keeping ALL those previous kernels? I only keep the one previous to the current, just in case. They do take up space and really serve no purpose. My suggestion is to install ubuntu-tweak and in the package cleaner section there is a function to remove kernels. There is really no need to keep them all and it will make the GRUB menu so much more smaller. You still have 10.04 kernels there and they should be deleted if you are running 11.04.

---

### Post by cinkler on 2011-08-26
I mentioned it above - they get installed when updating system, but are not visible in GRUB menu.

---

### Post by Enigmapond on 2011-08-26
The list is probably too long. As I stated, delete the older kernels and see if that fixes your problem. You don't need any but the current and the one previous.

---

### Post by cinkler on 2011-08-26
Here is output - essentially it again got error in grub.cfg, line 110:


[FONT="Courier New"]sudo apt-get remove linux-image-2.6.35-27-generic linux-image-2.6.38-8-generic linux-image-2.6.38-10-generic 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-image-2.6.35-27-generic linux-image-2.6.38-10-generic linux-image-2.6.38-8-generic
0 upgraded, 0 newly installed, 3 to remove and 3 not upgraded.
After this operation, 435 MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 392247 files and directories currently installed.)
Removing linux-image-2.6.35-27-generic ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 2.6.35-27-generic /boot/vmlinuz-2.6.35-27-generic
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.35-27-generic /boot/vmlinuz-2.6.35-27-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 2.6.35-27-generic /boot/vmlinuz-2.6.35-27-generic
Generating grub.cfg ...
Found background image: /usr/share/images/desktop-base/desktop-grub.png
Found linux image: /boot/vmlinuz-2.6.38-11-generic
Found initrd image: /boot/initrd.img-2.6.38-11-generic
Found linux image: /boot/vmlinuz-2.6.38-10-generic
Found initrd image: /boot/initrd.img-2.6.38-10-generic
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found linux image: /boot/vmlinuz-2.6.35-28-generic
Found initrd image: /boot/initrd.img-2.6.35-28-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda2
error: syntax error.
error: Incorrect command.
error: syntax error.
error: line no: 110
Syntax errors are detected in generated GRUB config file.
Ensure that there are no errors in /etc/default/grub
and /etc/grub.d/* files or please file a bug report with
/boot/grub/grub.cfg.new file attached.
done
Removing linux-image-2.6.38-10-generic ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
dkms: removing: virtualbox-ose 4.0.4 (2.6.38-10-generic) (x86_64)

-------- Uninstall Beginning --------
Module:  virtualbox-ose
Version: 4.0.4
Kernel:  2.6.38-10-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

vboxdrv.ko:
 - Uninstallation
   - Deleting from: /lib/modules/2.6.38-10-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

vboxnetadp.ko:
 - Uninstallation
   - Deleting from: /lib/modules/2.6.38-10-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

vboxnetflt.ko:
 - Uninstallation
   - Deleting from: /lib/modules/2.6.38-10-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.
depmod.......

DKMS: uninstall Completed.
dkms: removing: fglrx 8.840 (2.6.38-10-generic) (x86_64)

-------- Uninstall Beginning --------
Module:  fglrx
Version: 8.840
Kernel:  2.6.38-10-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

fglrx.ko:
 - Uninstallation
   - Deleting from: /lib/modules/2.6.38-10-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.
depmod....

DKMS: uninstall Completed.
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
Generating grub.cfg ...
Found background image: /usr/share/images/desktop-base/desktop-grub.png
Found linux image: /boot/vmlinuz-2.6.38-11-generic
Found initrd image: /boot/initrd.img-2.6.38-11-generic
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found linux image: /boot/vmlinuz-2.6.35-28-generic
Found initrd image: /boot/initrd.img-2.6.35-28-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda2
error: syntax error.
error: Incorrect command.
error: syntax error.
error: line no: 110
Syntax errors are detected in generated GRUB config file.
Ensure that there are no errors in /etc/default/grub
and /etc/grub.d/* files or please file a bug report with
/boot/grub/grub.cfg.new file attached.
done
The link /vmlinuz.old is a damaged link
Removing symbolic link vmlinuz.old 
 you may need to re-run your boot loader[grub]
The link /initrd.img.old is a damaged link
Removing symbolic link initrd.img.old 
 you may need to re-run your boot loader[grub]
Removing linux-image-2.6.38-8-generic ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 2.6.38-8-generic /boot/vmlinuz-2.6.38-8-generic
dkms: removing: fglrx 8.840 (2.6.38-8-generic) (x86_64)

-------- Uninstall Beginning --------
Module:  fglrx
Version: 8.840
Kernel:  2.6.38-8-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

fglrx.ko:
 - Uninstallation
   - Deleting from: /lib/modules/2.6.38-8-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.
depmod.......

DKMS: uninstall Completed.
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.38-8-generic /boot/vmlinuz-2.6.38-8-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 2.6.38-8-generic /boot/vmlinuz-2.6.38-8-generic
Generating grub.cfg ...
Found background image: /usr/share/images/desktop-base/desktop-grub.png
Found linux image: /boot/vmlinuz-2.6.38-11-generic
Found initrd image: /boot/initrd.img-2.6.38-11-generic
Found linux image: /boot/vmlinuz-2.6.35-28-generic
Found initrd image: /boot/initrd.img-2.6.35-28-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda2
error: syntax error.
error: Incorrect command.
error: syntax error.
error: line no: 110
Syntax errors are detected in generated GRUB config file.
Ensure that there are no errors in /etc/default/grub
and /etc/grub.d/* files or please file a bug report with
/boot/grub/grub.cfg.new file attached.
done
W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) natty/partner amd64 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_natty_partner_binary-amd64_Packages)
W: You may want to run apt-get update to correct these problems[/FONT]

---

### Post by oldfred on 2011-08-26
I had a typo in my 40_custom that still worked thru grub 1.98. But with grub 1.99 it would not update grub.cfg and copied the update to a grub.cfg.new file, so grub.cfg was not updated. Once I fixed typo then it worked.

Find the error in line 110 and after you fix it then it will update.

---

### Post by cinkler on 2011-08-26
Fixing syntax error in /etc/default/grub fixed the issue. 

1. I uninstalled unused kernels

2.I have removed this line:

video=uvesafb:mode_option=>>1400x1050-24<<,mtrr=3,scroll=ywrap

3. executed 

sudo update-grub

It fixed a number of issues:

a. I have different Debian background in boot menu
b. most recent kernel appeared in boot menu
c. first boot took took longer than usual
d. X booted in Unity (I didn't see it until now)
e. Alt-Tab still doesn't work.

So to summarize: syntax error in /etc/default/grub caused new kernels not to be included in GRUB menu and a bunch of other problems.

---

