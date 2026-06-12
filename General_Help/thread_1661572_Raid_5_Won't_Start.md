---
title: "Raid 5 Won't Start"
date: 2011-01-06
forum: General Help
---

### Post by jaytcarriere on 2011-01-06
Hi, 
I was running Ubuntu 9.10 with 3 - 1.5TB drives in a software Raid 5 array. The OS is installed to a separate drive. I decided to format the OS drive and install Ubuntu 10.10, but having done that I can no longer get my Raid array to start. When I am in the Disk Utility and hit the "Start RAID Array" button I get a message saying that there are not enough components to start the Raid array, even though the 3 raid drives show up within the Disk Utility. Any help would be greatly appreciated!

Thanks,
Jay

---

### Post by jaytcarriere on 2011-01-06
I just installed mdadm and used mdadm --assemble --scan, that allowed the raid drives to be detected and it seems to be working now.

Cheers,
Jay

---

