---
title: "USB Mount error"
date: 2010-12-12
forum: General Help
---

### Post by agamjain on 2010-12-12
I am trying to connect my Nokia 5800 to my laptop. When I connect, it shows two icons, one for the memory card and the other for the phone memory. I am unable to access the icon for the phone memory. I can access the memory card location, but when I try to copy something into it, I receive the following error: "There was an error copying the file into /media/usb0/download." And then it says Permission denied. Is it some problem with the mounting of the device? Kindly help me out with this problem.

---

### Post by rickyrockrat on 2010-12-12
Try running dmesg and see what it says. Alternatively you can tail /var/log/syslog

for either of these go to a terminal and type:
```
dmesg
```
or 
```
tail /var/log/syslog
```
If you want to watch what happens when you plug it in:
```
tail -f /var/log/syslog
```
Hit Ctrl-C to stop this last command.

Post the relevant messages about your device. Should start with something like waiting for storage media....

---

### Post by agamjain on 2010-12-12
This is the output I get when I type tail -f /var/log/syslog command after connecting my phone.
```
Dec 13 00:17:38 agam-Presario-V3000-RE032PA-AB0 kernel: [184846.892061] usb 1-5: new high speed USB device using ehci_hcd and address 15
Dec 13 00:17:38 agam-Presario-V3000-RE032PA-AB0 kernel: [184847.060681] scsi14 : usb-storage 1-5:1.0
Dec 13 00:17:39 agam-Presario-V3000-RE032PA-AB0 kernel: [184848.090749] scsi 14:0:0:0: Direct-Access     Nokia    S60              1.0  PQ: 0 ANSI: 0
Dec 13 00:17:39 agam-Presario-V3000-RE032PA-AB0 kernel: [184848.102687] sd 14:0:0:0: Attached scsi generic sg2 type 0
Dec 13 00:17:39 agam-Presario-V3000-RE032PA-AB0 kernel: [184848.129689] sd 14:0:0:0: [sdb] 7744512 512-byte logical blocks: (3.96 GB/3.69 GiB)
Dec 13 00:17:39 agam-Presario-V3000-RE032PA-AB0 kernel: [184848.130106] sd 14:0:0:0: [sdb] Write Protect is off
Dec 13 00:17:39 agam-Presario-V3000-RE032PA-AB0 kernel: [184848.130115] sd 14:0:0:0: [sdb] Mode Sense: 03 00 00 00
Dec 13 00:17:39 agam-Presario-V3000-RE032PA-AB0 kernel: [184848.130122] sd 14:0:0:0: [sdb] Assuming drive cache: write through
Dec 13 00:17:39 agam-Presario-V3000-RE032PA-AB0 kernel: [184848.135804] sd 14:0:0:0: [sdb] Assuming drive cache: write through
Dec 13 00:17:40 agam-Presario-V3000-RE032PA-AB0 kernel: [184848.135815]  sdb:
Dec 13 00:17:40 agam-Presario-V3000-RE032PA-AB0 kernel: [184848.406166] sd 14:0:0:0: [sdb] Assuming drive cache: write through
Dec 13 00:17:40 agam-Presario-V3000-RE032PA-AB0 kernel: [184848.406180] sd 14:0:0:0: [sdb] Attached SCSI removable disk
Dec 13 00:17:40 agam-Presario-V3000-RE032PA-AB0 usbmount[18582]: executing command: mount -tvfat -osync,noexec,nodev,noatime,nodiratime /dev/sdb /media/usb0
Dec 13 00:17:40 agam-Presario-V3000-RE032PA-AB0 usbmount[18582]: executing command: run-parts /etc/usbmount/mount.d
Dec 13 00:17:38 agam-Presario-V3000-RE032PA-AB0 kernel: [184846.892061] usb 1-5: new high speed USB device using ehci_hcd and address 15
Dec 13 00:17:38 agam-Presario-V3000-RE032PA-AB0 kernel: [184847.060681] scsi14 : usb-storage 1-5:1.0
Dec 13 00:17:39 agam-Presario-V3000-RE032PA-AB0 kernel: [184848.090749] scsi 14:0:0:0: Direct-Access     Nokia    S60              1.0  PQ: 0 ANSI: 0
Dec 13 00:17:39 agam-Presario-V3000-RE032PA-AB0 kernel: [184848.102687] sd 14:0:0:0: Attached scsi generic sg2 type 0
Dec 13 00:17:39 agam-Presario-V3000-RE032PA-AB0 kernel: [184848.129689] sd 14:0:0:0: [sdb] 7744512 512-byte logical blocks: (3.96 GB/3.69 GiB)
Dec 13 00:17:39 agam-Presario-V3000-RE032PA-AB0 kernel: [184848.130106] sd 14:0:0:0: [sdb] Write Protect is off
Dec 13 00:17:39 agam-Presario-V3000-RE032PA-AB0 kernel: [184848.130115] sd 14:0:0:0: [sdb] Mode Sense: 03 00 00 00
Dec 13 00:17:39 agam-Presario-V3000-RE032PA-AB0 kernel: [184848.130122] sd 14:0:0:0: [sdb] Assuming drive cache: write through
Dec 13 00:17:39 agam-Presario-V3000-RE032PA-AB0 kernel: [184848.135804] sd 14:0:0:0: [sdb] Assuming drive cache: write through
Dec 13 00:17:40 agam-Presario-V3000-RE032PA-AB0 kernel: [184848.135815]  sdb:
Dec 13 00:17:40 agam-Presario-V3000-RE032PA-AB0 kernel: [184848.406166] sd 14:0:0:0: [sdb] Assuming drive cache: write through
Dec 13 00:17:40 agam-Presario-V3000-RE032PA-AB0 kernel: [184848.406180] sd 14:0:0:0: [sdb] Attached SCSI removable disk
Dec 13 00:17:40 agam-Presario-V3000-RE032PA-AB0 usbmount[18582]: executing command: mount -tvfat -osync,noexec,nodev,noatime,nodiratime /dev/sdb /media/usb0
Dec 13 00:17:40 agam-Presario-V3000-RE032PA-AB0 usbmount[18582]: executing command: run-parts /etc/usbmount/mDec 13 00:17:38 agam-Presario-V3000-RE032PA-AB0 kernel: [184846.892061] usb 1-5: new high speed USB device using ehci_hcd and address 15
Dec 13 00:17:38 agam-Presario-V3000-RE032PA-AB0 kernel: [184847.060681] scsi14 : usb-storage 1-5:1.0
Dec 13 00:17:39 agam-Presario-V3000-RE032PA-AB0 kernel: [184848.090749] scsi 14:0:0:0: Direct-Access     Nokia    S60              1.0  PQ: 0 ANSI: 0
Dec 13 00:17:39 agam-Presario-V3000-RE032PA-AB0 kernel: [184848.102687] sd 14:0:0:0: Attached scsi generic sg2 type 0
Dec 13 00:17:39 agam-Presario-V3000-RE032PA-AB0 kernel: [184848.129689] sd 14:0:0:0: [sdb] 7744512 512-byte logical blocks: (3.96 GB/3.69 GiB)
Dec 13 00:17:39 agam-Presario-V3000-RE032PA-AB0 kernel: [184848.130106] sd 14:0:0:0: [sdb] Write Protect is off
Dec 13 00:17:39 agam-Presario-V3000-RE032PA-AB0 kernel: [184848.130115] sd 14:0:0:0: [sdb] Mode Sense: 03 00 00 00
Dec 13 00:17:39 agam-Presario-V3000-RE032PA-AB0 kernel: [184848.130122] sd 14:0:0:0: [sdb] Assuming drive cache: write through
Dec 13 00:17:39 agam-Presario-V3000-RE032PA-AB0 kernel: [184848.135804] sd 14:0:0:0: [sdb] Assuming drive cache: write through
Dec 13 00:17:40 agam-Presario-V3000-RE032PA-AB0 kernel: [184848.135815]  sdb:
Dec 13 00:17:40 agam-Presario-V3000-RE032PA-AB0 kernel: [184848.406166] sd 14:0:0:0: [sdb] Assuming drive cache: write through
Dec 13 00:17:40 agam-Presario-V3000-RE032PA-AB0 kernel: [184848.406180] sd 14:0:0:0: [sdb] Attached SCSI removable disk
Dec 13 00:17:40 agam-Presario-V3000-RE032PA-AB0 usbmount[18582]: executing command: mount -tvfat -osync,noexec,nodev,noatime,nodiratime /dev/sdb /media/usb0
Dec 13 00:17:40 agam-Presario-V3000-RE032PA-AB0 usbmount[18582]: executing command: run-parts /etc/usbmount/mount.d
Dec 13 00:17:38 agam-Presario-V3000-RE032PA-AB0 kernel: [184846.892061] usb 1-5: new high speed USB device using ehci_hcd and address 15
Dec 13 00:17:38 agam-Presario-V3000-RE032PA-AB0 kernel: [184847.060681] scsi14 : usb-storage 1-5:1.0
Dec 13 00:17:39 agam-Presario-V3000-RE032PA-AB0 kernel: [184848.090749] scsi 14:0:0:0: Direct-Access     Nokia    S60              1.0  PQ: 0 ANSI: 0
Dec 13 00:17:39 agam-Presario-V3000-RE032PA-AB0 kernel: [184848.102687] sd 14:0:0:0: Attached scsi generic sg2 type 0
Dec 13 00:17:39 agam-Presario-V3000-RE032PA-AB0 kernel: [184848.129689] sd 14:0:0:0: [sdb] 7744512 512-byte logical blocks: (3.96 GB/3.69 Gi
```

---

### Post by agamjain on 2010-12-12
And after that I get this:

```
B)
Dec 13 00:17:39 agam-Presario-V3000-RE032PA-AB0 kernel: [184848.130106] sd 14:0:0:0: [sdb] Write Protect is off
Dec 13 00:17:39 agam-Presario-V3000-RE032PA-AB0 kernel: [184848.130115] sd 14:0:0:0: [sdb] Mode Sense: 03 00 00 00
Dec 13 00:17:39 agam-Presario-V3000-RE032PA-AB0 kernel: [184848.130122] sd 14:0:0:0: [sdb] Assuming drive cache: write through
Dec 13 00:17:39 agam-Presario-V3000-RE032PA-AB0 kernel: [184848.135804] sd 14:0:0:0: [sdb] Assuming drive cache: write through
Dec 13 00:17:40 agam-Presario-V3000-RE032PA-AB0 kernel: [184848.135815]  sdb:
Dec 13 00:17:40 agam-Presario-V3000-RE032PA-AB0 kernel: [184848.406166] sd 14:0:0:0: [sdb] Assuming drive cache: write through
Dec 13 00:17:40 agam-Presario-V3000-RE032PA-AB0 kernel: [184848.406180] sd 14:0:0:0: [sdb] Attached SCSI removable disk
Dec 13 00:17:40 agam-Presario-V3000-RE032PA-AB0 usbmount[18582]: executing command: mount -tvfat -osync,noexec,nodev,noatime,nodiratime /dev/sdb /media/usb0
Dec 13 00:17:40 agam-Presario-V3000-RE032PA-AB0 usbmount[18582]: executing command: run-parts /etc/usbmount/mount.d
Dec 13 00:17:38 agam-Presario-V3000-RE032PA-AB0 kernel: [184846.892061] usb 1-5: new high speed USB device using ehci_hcd and address 15
Dec 13 00:17:38 agam-Presario-V3000-RE032PA-AB0 kernel: [184847.060681] scsi14 : usb-storage 1-5:1.0
Dec 13 00:17:39 agam-Presario-V3000-RE032PA-AB0 kernel: [184848.090749] scsi 14:0:0:0: Direct-Access     Nokia    S60              1.0  PQ: 0 ANSI: 0
Dec 13 00:17:39 agam-Presario-V3000-RE032PA-AB0 kernel: [184848.102687] sd 14:0:0:0: Attached scsi generic sg2 type 0
Dec 13 00:17:39 agam-Presario-V3000-RE032PA-AB0 kernel: [184848.129689] sd 14:0:0:0: [sdb] 7744512 512-byte logical blocks: (3.96 GB/3.69 GiDec 13 00:20:02 agam-Presario-V3000-RE032PA-AB0 ntpd[1147]: synchronized to 193.79.237.14, stratum 1
Dec 13 00:23:38 agam-Presario-V3000-RE032PA-AB0 sudo: pam_sm_authenticate: Called
Dec 13 00:23:38 agam-Presario-V3000-RE032PA-AB0 sudo: pam_sm_authenticate: username = [agam]
Dec 13 00:23:38 agam-Presario-V3000-RE032PA-AB0 sudo: pam_sm_authenticate: /home/agam is already mounted
Dec 13 00:23:44 agam-Presario-V3000-RE032PA-AB0 acpid: client connected from 18727[115:125]
Dec 13 00:23:44 agam-Presario-V3000-RE032PA-AB0 acpid: 1 client rule loaded
Dec 13 00:25:54 agam-Presario-V3000-RE032PA-AB0 ntpd[1147]: synchronized to 192.36.143.150, stratum 1
Dec 13 00:26:31 agam-Presario-V3000-RE032PA-AB0 udevd[413]: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /etc/udev/rules.d/01-mountmanager.rules:2
Dec 13 00:26:31 agam-Presario-V3000-RE032PA-AB0 udevd[413]: BUS= will be removed in a future udev version, please use SUBSYSTEM= to match the event device, or SUBSYSTEMS= to match a parent device, in /etc/udev/rules.d/01-mountmanager.rules:2
Dec 13 00:26:31 agam-Presario-V3000-RE032PA-AB0 udevd[413]: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /etc/udev/rules.d/01-mountmanager.rules:4
Dec 13 00:26:31 agam-Presario-V3000-RE032PA-AB0 udevd[413]: BUS= will be removed in a future udev version, please use SUBSYSTEM= to match the event device, or SUBSYSTEMS= to match a parent device, in /etc/udev/rules.d/01-mountmanager.rules:4
Dec 13 00:26:31 agam-Presario-V3000-RE032PA-AB0 udevd[413]: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /etc/udev/rules.d/01-mountmanager.rules:6
Dec 13 00:26:31 agam-Presario-V3000-RE032PA-AB0 udevd[413]: BUS= will be removed in a future udev version, please use SUBSYSTEM= to match the event device, or SUBSYSTEMS= to match a parent device, in /etc/udev/rules.d/01-mountmanager.rules:6
Dec 13 00:26:31 agam-Presario-V3000-RE032PA-AB0 udevd[413]: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /etc/udev/rules.d/01-mountmanager.rules:8
Dec 13 00:26:31 agam-Presario-V3000-RE032PA-AB0 udevd[413]: BUS= will be removed in a future udev version, please use SUBSYSTEM= to match the event device, or SUBSYSTEMS= to match a parent device, in /etc/udev/rules.d/01-mountmanager.rules:8
Dec 13 00:27:14 agam-Presario-V3000-RE032PA-AB0 ntpd_initres[1151]: host name not found: time.esec.com.au
```

---

