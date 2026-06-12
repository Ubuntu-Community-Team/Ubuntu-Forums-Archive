---
title: "VirtualBox fixed hard disk"
date: 2009-12-05
forum: General Help
---

### Post by raphaelmsx on 2009-12-05
Hello,

I'm using Ubuntu 9.10 and just installed VirtualBox from Synaptic.

When I created one 1GB and another 2GB virtual HDs and selected the option to pre-allocate the HD physically, everything went fine.

But, then, I did the same with a 4GB virtual HD, and it got stuck on the "creating fixed hard disk storage unit...". It's been at least 2 hours, and it's still 0% and I can't even cancel it, when I click the cancel button, nothing happens.

I'm using ext3 with encrypted /home.

What should I do?

Thank you!

---

### Post by Sin@Sin-Sacrifice on 2009-12-05
killall virtualbox or you can open System Monitor and kill it that way. Sounds like it may just have hiccuped.

---

### Post by raphaelmsx on 2009-12-06
> **Sin@Sin-Sacrifice said:**
> killall virtualbox or you can open System Monitor and kill it that way. Sounds like it may just have hiccuped.

did that, restarted ubuntu, opened virtualbox and system monitor. The same thing again. In system monitor VBoxSVC eats 90% and some times more than 100% of CPU, the status is sleeping (but sometimes running), memory 3.4 MiB, and waiting channel: futex_wait_queue_me. The VirtualBox process is almost the same, but always 0% CPU and 31.6MiB and the VBoxXCOMIPCD the waiting channel is poll_schedule_timeout.

I can successfully create a fixed HD of less size, such as 2GB, but 4GB always stuck on 0% ...

---

### Post by raphaelmsx on 2009-12-17
bump

---

### Post by nickrivers on 2010-02-16
Hi, i had the same problem but good for me i've solved it.
Same configuration "ext3 with encrypted /home".
Same problem "VBoxSVC eats 90% of CPU".

What have I done? I only change saving directory of the virtual disk.

---

### Post by omaralqady on 2010-02-17
Thank you very much :) I had the same problem and your solution worked for me :) Thanks again

---

