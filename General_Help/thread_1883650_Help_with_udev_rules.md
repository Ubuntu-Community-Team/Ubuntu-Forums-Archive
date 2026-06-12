---
title: "Help with udev rules"
date: 2011-11-19
forum: General Help
---

### Post by jaykumar_2001 on 2011-11-19
I need help with setting up a udev rule which 

1. Mount (at location /media/volume_name) any USB storage device with permission to specific group (adm)

2. Reconfigure samba to share /media/volume_name (restart smb daemon if required)

3. Reconfigure nfsd and made appropriate entries in /etc/exports (again restart nfsd if required)

4. Reconfigure media server (not sure which one)

This function is available on most opensource router OS (openwrt/gargoyle) for devices with support for usb storage.

---

