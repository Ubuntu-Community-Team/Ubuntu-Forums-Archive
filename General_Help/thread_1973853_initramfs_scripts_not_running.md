---
title: "initramfs scripts not running?"
date: 2012-05-05
forum: General Help
---

### Post by RoadEnds on 2012-05-05
I'm trying to create an initramfs script (for vgaswitcheroo).  The script I created functions correctly when executed on the CLI.  I placed it in the /usr/share/initramfs-tools/scripts/nfs-top directory and set the executable bit.  The owership/permissions match all of the other initramfs scripts.

Upon boot, I cannot find any evidence of these script running in dmesg, /var/log/syslog, nor /var/log/boot.log.  I see something flash on my screen which I believe *may* be the initramfs scripts (sub-second), however this boot process is masked by a splash screen which I cannot disable (help query out on separate forum post for that issue).

Does anyone know in which log file I would be able to find the initramfs logs to troubleshoot this issue?  Or a way to enable more verbose reporting from initramfs-tools?  My scripts already outputs debug information, but none of this is gets captured in logs.  I am not even positive that the script is even running at startup.

Thanks in advance.

---

