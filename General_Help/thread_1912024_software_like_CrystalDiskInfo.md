---
title: "software like CrystalDiskInfo"
date: 2012-01-19
forum: General Help
---

### Post by donald73d on 2012-01-19
I would like to run Ubuntu but need it to run software like crystaldiskinfo to display the health of a hard disk?  It does not appear that crystaldiskinfo runs on Linux.

---

### Post by raja.genupula on 2012-01-19
[http://blog.shadypixel.com/monitoring-hard-drive-health-on-linux-with-smartmontools/](http://blog.shadypixel.com/monitoring-hard-drive-health-on-linux-with-smartmontools/)

---

### Post by Buntumatic on 2012-01-19
Right, to see the most relevant info run ```
smartctl --all /dev/sda | grep -e "Reallocated_Sector_Ct" -e "Current_Pending_Sector" -e "Offline_Uncorrectable" -e "UDMA_CRC_Error_Count" -e "Hardware_ECC_Recovered"
```
for sda.

---

