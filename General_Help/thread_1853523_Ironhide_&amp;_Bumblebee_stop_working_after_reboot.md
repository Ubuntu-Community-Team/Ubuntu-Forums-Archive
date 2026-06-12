---
title: "Ironhide &amp; Bumblebee stop working after reboot"
date: 2011-10-02
forum: General Help
---

### Post by stepheny on 2011-10-02
I recently found Ironhide as a replacement for Bumblebee which unaccountably stopped working after an Update Manager driven update to kernel 2.6.38-11, see this post [http://ubuntuforums.org/showthread.php?t=1831892](http://ubuntuforums.org/showthread.php?t=1831892)

I purged Bumblebee but it still appeared when I ran ```
service --status-all
``` so Ithen removed the bumblebee* files from etc/init.d and etc/default. Why they weren't removed by purge I'm not sure.

After that I purged nvidia-current and re-booted. I then installed ironhide and configured it. Everything then ran perfectly and by running ```
optirun glxgears
``` I was able to switch the nividia card on. However when I tried ```
optirun glxgears
``` after a reboot I got the message ```
FATAL: Error inserting nvidia_current (/lib/modules/2.6.38-11-generic-pae/updates/dkms/nvidia-current.ko): No such device

```

I completely removed nvidia-current and ironhide, rebooted and then installed nvidia-current. By running ```
sudo modprobe nvidia-current
``` the module was loaded. Running ```
sudo modprobe nvidia-current
``` also loaded the module after a reboot. I then installed ironhide and everything was fine. However after a reboot I got the message ```
FATAL: Error inserting nvidia_current (/lib/modules/2.6.38-11-generic-pae/updates/dkms/nvidia-current.ko): No such device

``` again and running ```
sudo modprobe nvidia-current
``` gave the message ```
FATAL: Error inserting nvidia_current (/lib/modules/2.6.38-11-generic-pae/updates/dkms/nvidia-current.ko): No such device

```

It seems that on startup my machine is loading something that is stopping nvidia-current from working but only if ironhide or bumblebee are installed.

---

### Post by Boris_Brodski on 2011-10-10
Hello!

I experience almost the same problem.

Beside that, the suspend is not working and the system freezes,
if I connect my printer over USB.

Did you solved the problem somehow?

boris@Boris-Dell:~$ uname -a
Linux Boris-Dell 2.6.38-11-generic #50-Ubuntu SMP Mon Sep 12 21:17:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
 
Laptop: DELL XPS 17 L702x

Thank you very much for help!

---

### Post by LowDepth on 2011-10-13
Same problem, different machine:

```
uname -a:
2.6.38-11-generic #50-Ubuntu SMP Mon Sep 12 21:17:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
```

XPS15 L502x

---

### Post by adrien214 on 2011-11-23
I had the same problem. Then I didn't. I could run optirun glxgears and the terminal would show that ironhide started properly and the nvidia card was on. Then I stopped it. Ironhide successfully shut down the nvidia. Then I tried to turn it on again and it wouldn't display the ironhide or nvidia info, just the glxgears fps... now I'm like wut?

---

