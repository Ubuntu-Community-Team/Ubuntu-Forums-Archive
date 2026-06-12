---
title: "Harddrive issues"
date: 2009-10-28
forum: General Help
---

### Post by logikz on 2009-10-28
how can this be possible for 1 disk?  I formatted as 1 root and 1 swap.  sda1, sda2 > extended sda5.  Now its this?  Seems odd, it was a brand new hard drive.
  Any way i could fix?

root@online:/dev/disk/by-id# kpartx                                         
ata-WDC_WD3200AAKS-00L9A0_WD-WCAV24661468                                   
ata-WDC_WD3200AAKS-00L9A0_WD-WCAV24661468-part1                             
ata-WDC_WD3200AAKS-00L9A0_WD-WCAV24661468-part2                             
dm-name-1ATA_WDC_WD3200AAKS-00L9A0_WD-WCAV24661468                          
dm-name-1ATA_WDC_WD3200AAKS-00L9A0_WD-WCAV24661468-part1                    
dm-name-1ATA_WDC_WD3200AAKS-00L9A0_WD-WCAV24661468-part2                    
dm-uuid-mpath-1ATA_WDC_WD3200AAKS-00L9A0_WD-WCAV24661468                    
dm-uuid-part1-mpath-1ATA_WDC_WD3200AAKS-00L9A0_WD-WCAV24661468              
dm-uuid-part2-mpath-1ATA_WDC_WD3200AAKS-00L9A0_WD-WCAV24661468              
scsi-1ATA_WDC_WD3200AAKS-00L9A0_WD-WCAV24661468                             
scsi-1ATA_WDC_WD3200AAKS-00L9A0_WD-WCAV24661468-part1                       
scsi-1ATA_WDC_WD3200AAKS-00L9A0_WD-WCAV24661468-part2                       
scsi-SATA_WDC_WD3200AAKS-_WD-WCAV24661468                                   
scsi-SATA_WDC_WD3200AAKS-_WD-WCAV24661468-part1                             
scsi-SATA_WDC_WD3200AAKS-_WD-WCAV24661468-part2

---

### Post by falconindy on 2009-10-28
No idea what kpartx is. Posting the output of a standard diagnostic tool like `fdisk -l` is a lot more useful.

---

