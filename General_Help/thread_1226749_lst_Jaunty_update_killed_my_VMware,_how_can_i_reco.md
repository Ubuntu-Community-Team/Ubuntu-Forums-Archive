---
title: "lst Jaunty update killed my VMware, how can i recompile"
date: 2009-07-29
forum: General Help
---

### Post by Ordes on 2009-07-29
After the last update, yesterday 07-30, my vmware is not working properly anymore.

As after every update, vmware toled my to recompile the kernel (click OK). However some parts could not be recompiled this time. So when i start up VMware my eth is not working. --> "cannot open /dev/vmnet/

The basic VMmachine is running though.

Restarting vmware didnt bring up the recompile dialog.

Uninstalling and reinstalling vmware didnt bring up the recompile dialog. So after uninstalling i tried:

$ locate vmware:
/etc/vmware
/etc/init.d/vmware
/etc/rc2.d/K08vmware
/etc/rc2.d/S19vmware
/etc/rc3.d/K08vmware
/etc/rc3.d/S19vmware
/etc/rc5.d/K08vmware
/etc/rc5.d/S19vmware
/etc/vmware/bootstrap
/etc/vmware/components
/etc/vmware/config
/etc/vmware/database
/etc/vmware/networking
/etc/vmware/vmnet1
/etc/vmware/vmnet8
/etc/xdg/menus/applications-merged/vmware-ace-vms.menu
/usr/bin/vmware
/usr/bin/vmware-acetool
/usr/bin/vmware-gksu
/usr/bin/vmware-modconfig
/usr/bin/vmware-mount
/usr/bin/vmware-netcfg
/usr/bin/vmware-networks
/usr/bin/vmware-ping
/usr/bin/vmware-remotemks
/usr/bin/vmware-tray
/usr/bin/vmware-uninstall
/usr/bin/vmware-unity-helper
/usr/bin/vmware-vdiskmanager
/usr/include/vmware-vix
/usr/lib/vmware
/usr/lib/vmware-vix
/usr/lib/xorg/modules/drivers/vmware_drv.so
/usr/sbin/vmware-authd
/usr/share/app-install/desktop/vmware-user.desktop
/usr/share/app-install/icons/_usr_share_pixmaps_vmware-player.png
/usr/share/applications/vmware-netcfg.desktop
/usr/share/applications/vmware-player.desktop
/usr/share/applications/vmware-workstation.desktop
/usr/share/bug/xserver-xorg-video-vmware
/usr/share/bug/xserver-xorg-video-vmware/script
/usr/share/desktop-directories/vmware-ace-vms.directory
/usr/share/doc/vmware-player
/usr/share/doc/vmware-vix
/usr/share/doc/vmware-workstation
/usr/share/doc/xserver-xorg-video-vmware
/usr/share/doc/xserver-xorg-video-vmware/changelog.Debian.gz
/usr/share/doc/xserver-xorg-video-vmware/changelog.gz
/usr/share/doc/xserver-xorg-video-vmware/copyright
/usr/share/icons/hicolor/16x16/apps/vmware-acevm.png
/usr/share/icons/hicolor/16x16/apps/vmware-netcfg.png
/usr/share/icons/hicolor/16x16/apps/vmware-player.png
/usr/share/icons/hicolor/16x16/apps/vmware-workstation.png
/usr/share/icons/hicolor/16x16/mimetypes/application-x-vmware-team.png
/usr/share/icons/hicolor/16x16/mimetypes/application-x-vmware-vm-clone.png
/usr/share/icons/hicolor/16x16/mimetypes/application-x-vmware-vm-legacy.png
/usr/share/icons/hicolor/16x16/mimetypes/application-x-vmware-vm.png
/usr/share/icons/hicolor/24x24/apps/vmware-acevm.png
/usr/share/icons/hicolor/24x24/apps/vmware-netcfg.png
/usr/share/icons/hicolor/24x24/apps/vmware-player.png
/usr/share/icons/hicolor/24x24/apps/vmware-workstation.png
/usr/share/icons/hicolor/24x24/mimetypes/application-x-vmware-vm-clone.png
/usr/share/icons/hicolor/24x24/mimetypes/application-x-vmware-vm.png
/usr/share/icons/hicolor/32x32/apps/vmware-player.png
/usr/share/icons/hicolor/32x32/apps/vmware-workstation.png
/usr/share/icons/hicolor/48x48/apps/vmware-acevm.png
/usr/share/icons/hicolor/48x48/apps/vmware-player.png
/usr/share/icons/hicolor/48x48/apps/vmware-workstation.png
/usr/share/icons/hicolor/48x48/mimetypes/application-x-vmware-snapshot.png
/usr/share/icons/hicolor/48x48/mimetypes/application-x-vmware-team.png
/usr/share/icons/hicolor/48x48/mimetypes/application-x-vmware-vm.png
/usr/share/icons/hicolor/48x48/mimetypes/application-x-vmware-vmdisk.png
/usr/share/icons/hicolor/48x48/mimetypes/application-x-vmware-vmfoundry.png
/usr/share/icons/hicolor/scalable/apps/vmware-acevm.svg
/usr/share/icons/hicolor/scalable/apps/vmware-player.svg
/usr/share/icons/hicolor/scalable/apps/vmware-workstation.svg
/usr/share/icons/hicolor/scalable/mimetypes/application-x-vmware-snapshot.svg
/usr/share/icons/hicolor/scalable/mimetypes/application-x-vmware-team.svg
/usr/share/icons/hicolor/scalable/mimetypes/application-x-vmware-vm-clone.svg
/usr/share/icons/hicolor/scalable/mimetypes/application-x-vmware-vm-legacy.svg
/usr/share/icons/hicolor/scalable/mimetypes/application-x-vmware-vm.svg
/usr/share/icons/hicolor/scalable/mimetypes/application-x-vmware-vmfoundry.svg
/usr/share/man/man1/vmware.1.gz
/usr/share/man/man4/vmware.4.gz
/usr/share/mime/application/x-vmware-snapshot.xml
/usr/share/mime/application/x-vmware-team.xml
/usr/share/mime/application/x-vmware-vm.xml
/usr/share/mime/application/x-vmware-vmdisk.xml
/usr/share/mime/application/x-vmware-vmfoundry.xml
/usr/share/mime/packages/vmware-player.xml
/usr/share/xserver-xorg/pci/vmware.ids
/usr/src/linux-headers-2.6.28-11/arch/x86/include/asm/vmware.h
/usr/src/linux-headers-2.6.28-13/arch/x86/include/asm/vmware.h
/var/lib/dpkg/info/xserver-xorg-video-vmware.list
/var/lib/dpkg/info/xserver-xorg-video-vmware.md5sums
/var/log/vmware-installer

so all those files are left. 
Shall i manualy delete them? If so which ones? All?

Or how can i just retry the compile process?
Cuz they told me to look at the recomile error log. But i clicked over it, and couldnt find it anymore.:(

---

### Post by dcstar on 2009-07-30
> **Ordes said:**
> After the last update, yesterday 07-30, my vmware is not working properly anymore.

As after every update, vmware toled my to recompile the kernel (click OK). However some parts could not be recompiled this time. So when i start up VMware my eth is not working. --> "cannot open /dev/vmnet/

The basic VMmachine is running though.

Restarting vmware didnt bring up the recompile dialog.

Uninstalling and reinstalling vmware didnt bring up the recompile dialog. So after uninstalling i tried:
...........
Or how can i just retry the compile process?
Cuz they told me to look at the recomile error log. But i clicked over it, and couldnt find it anymore.:(

Go to the Virtualization forum and look in the Mega-thread.

---

### Post by Ordes on 2009-10-14
removed VM-Ware, using Virtual Box, seems to work better....

---

