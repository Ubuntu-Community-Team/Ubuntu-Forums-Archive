---
title: "USB Broken in 10.04"
date: 2010-09-03
forum: General Help
---

### Post by joeknoodle on 2010-09-03
Ubuntu 10.04 / Gnome  So, I have some usb drives and such, and they don't mount properly. I've tried the following fixes:  1- In the BIOS I've enabled "USB Legacy" support, as well as turned OFF the ability to boot to USB devices. I've also made sure to never have a bootable USB device in the slot since this seems to cause a problem with my BIOS.  2- Turn off the floppy module, and then restart usb_storage module, but this fix is flaky at best...  This fix works sometimes, but most often not.  When I can get the USB to mount, it fails to mount again on restart.  Questions:  Is Ubuntu 10.04 broken regarding USB devices?  If not, what will fix this problem?

---

### Post by lz1dsb on 2010-09-03
Just a quick question. When you insert a USB while running Ubuntu, can you see anything with the console command: lsusb?
This command shows you anything that is connected on the USB bus, you would also see some internal devices though. 

Cheers, 
Boyan

---

### Post by joeknoodle on 2010-09-03
Thanks for the reply.  Check lsusb right now...  lsusb returns:  ```
 Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
``` When devices do manage to mount, that does change.  (edit to fix code tags)

---

### Post by joeknoodle on 2010-09-03
Out of curiosity I just did...    Restarted  did the floppy off and usb_storage modprobes  No dice   So I opened Config Editor    There I turned off auto-mount, and turned off auto-open  Then I turned them back on  Now I have usb drive    lsusb returns:   Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  Bus 002 Device 002: ID 1058:070a Western Digital Technologies, Inc.  Bus 002  Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub   Thoughts?  Edit in  I apologize for the formatting if it's all weird, and I can't tell if its on my end or the forum's end

---

