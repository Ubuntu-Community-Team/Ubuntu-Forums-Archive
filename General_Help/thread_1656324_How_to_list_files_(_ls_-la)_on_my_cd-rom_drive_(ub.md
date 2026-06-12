---
title: "How to list files ( ls -la) on my cd-rom drive (ubuntu 8.04)"
date: 2010-12-30
forum: General Help
---

### Post by xr4ti on 2010-12-30
How can I list all (ls -la) files on a cd?  Here is my cd dmesg output:

<code>
[  351.766423] scsi 5:0:0:0: CD-ROM            Memorex  DVD+-RAM 530L v1 5M64 PQ: 0 ANSI: 0
[  351.861991] sr0: scsi3-mmc drive: 125x/125x writer dvd-ram cd/rw xa/form2 cdda tray
[  351.861994] Uniform CD-ROM driver Revision: 3.20
[  351.862029] sr 5:0:0:0: Attached scsi CD-ROM sr0
[  828.247516] usb 5-3: new high speed USB device using ehci_hcd and address 3
[  841.280357] usb 5-3: new high speed USB device using ehci_hcd and address 4
[  918.624416] usb 5-3: new high speed USB device using ehci_hcd and address 5
[   31.044889] ehci_hcd 0000:00:1d.7: debug port 1
[  104.522516] usb 5-3: new high speed USB device using ehci_hcd and address 6


</code>

---

### Post by Nytram on 2010-12-30
Removable media including Cd's are usually auto-mounted under the /media directory.

---

