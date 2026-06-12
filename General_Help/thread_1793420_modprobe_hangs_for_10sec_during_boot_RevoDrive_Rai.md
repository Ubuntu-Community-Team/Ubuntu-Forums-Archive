---
title: "modprobe hangs for 10sec during boot RevoDrive Raid 0"
date: 2011-06-29
forum: General Help
---

### Post by markp1989 on 2011-06-29
just got my OCZ revo drive in the post today. 

fyi: the 50gb revo drive is 2x25gb SSDs + a fake raid controller on a PCIE card. 
[http://www.play.com/PC/PCs/4-/18616749/OCZ-OCZSSDPX-1RVD0050-Revo-PCI-Express-4x-Solid-State-Hard-Drive-SSD-50GB/Product.html?_%24ja=tsid:11518|cat:18616749|prd:18616749](http://www.play.com/PC/PCs/4-/18616749/OCZ-OCZSSDPX-1RVD0050-Revo-PCI-Express-4x-Solid-State-Hard-Drive-SSD-50GB/Product.html?_%24ja=tsid:11518|cat:18616749|prd:18616749)

I set up 100mb at the start of the first "drive" for /boot , and used the rest of the drive in raid 0 with the 2nd drive. 

here is the boot chart, you can see most of the boot time is modprobe, hanging for 10 seconds.


[https://dl.dropbox.com/s/e14gr1fu2pvnlv2/MarksPC-natty-20110629-3.png](https://dl.dropbox.com/s/e14gr1fu2pvnlv2/MarksPC-natty-20110629-3.png)

is there anyway I can stop modprobe hanging like that?

Thanks, Mark

---

