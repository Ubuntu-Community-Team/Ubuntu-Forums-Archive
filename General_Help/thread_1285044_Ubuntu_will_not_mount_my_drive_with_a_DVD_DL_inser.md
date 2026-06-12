---
title: "Ubuntu will not mount my drive with a DVD DL inserted"
date: 2009-10-07
forum: General Help
---

### Post by 98cwitr on 2009-10-07
Trying to burn a big ISO and Ubuntu will not mount the drive. I searched google and this forum and did not find any things specific to the problem. My drive does support DVD DLs. Thanks.

---

### Post by 98cwitr on 2009-10-07
*-cdrom
                   description: DVD-RAM writer
                   product: DVD-RAM GSA-H55N
                   vendor: HL-DT-ST
                   physical id: 0.0.0
                   bus info: scsi@4:0.0.0
                   logical name: /dev/cdrom
                   logical name: /dev/cdrw
                   logical name: /dev/dvd
                   logical name: /dev/dvdrw
                   logical name: /dev/scd0
                   logical name: /dev/sr0
                   version: 1.00
                   serial: [HL-DT-STDVD-RAM GSA-H55N1.0007/03/21 7U02
                   capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                   configuration: ansiversion=5 status=ready
                 *-medium
                      physical id: 0
                      logical name: /dev/cdrom


DVD DL is not listed, but I am able to use DL functionality under windows :/ I don't have a problem with DVD+Rs


nm, searched some more and found a known problem w/ using memorex disks... lo and behold thats what im using, please close

---

