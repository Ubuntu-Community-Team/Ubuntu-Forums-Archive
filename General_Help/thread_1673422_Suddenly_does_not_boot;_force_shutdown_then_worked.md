---
title: "Suddenly does not boot; force shutdown then worked"
date: 2011-01-22
forum: General Help
---

### Post by 3602 on 2011-01-22
So I just booted my computer. The Plymouth screen was there as usual, but after a while it didn't go away. There was the white "ubuntu" and five orange points. The points are all orange and are not moving. There was no disk activity.
It remained so for several minutes. Seeing no progress, I held down the power button for a force shutdown, then I booted it again. It worked so now I'm writing this.
Last shutdown was normal through Gnome. Last time I did not apply changes to the system (no softwares nor updates installed). What should I do?
This is the first time that it happens since I installed Ubuntu on this computer. I know that back in Jaunty, after a predetermined number of boots the system performs a disk check. Could it be? But there was no message on the screen and nothing audible from the disk.
Thank you very much.

---

### Post by 3602 on 2011-01-22
Well I just found out that I have 3 kernels installed: 35-22, 35-24 and 35-25. I'm on 35-25, I removed 35-22 through Synaptic (there was the kernel file, but no headers file, weird) and kept 35-24 as a fall-back position. Updated Grub2 then rebooted, no problems.
I'm not saying that this is the problem. Some people somewhere pointed out that occasional boot hiccups can be traced to BIOS or hard drive, or graphics drivers. So, a little hiccup or a potential serious problem ahead?

---

