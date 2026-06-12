---
title: "Hang on shutdown... How do I check what's wrong?"
date: 2012-03-19
forum: General Help
---

### Post by jonashendrickx on 2012-03-19
My Ubuntu 11.10 hangs on shutdown.

I have a ATI card installed with fglrx-updates installed.
I know ATI is crap with linux

[http://ubuntuforums.org/showthread.php?t=808543](http://ubuntuforums.org/showthread.php?t=808543)

I however found this thread. Ubuntu 11.10 uses lightdm. While there is no lightdm in that file he is describing... Maybe that is the issue preventing to shut down?

Is there a way for me to find out what exactly is going wrong? a log file I could explore?

---

### Post by plucky on 2012-03-19
> **jonashendrickx said:**
> My Ubuntu 11.10 hangs on shutdown.

I have a ATI card installed with fglrx-updates installed.
I know ATI is crap with linux

[http://ubuntuforums.org/showthread.php?t=808543](http://ubuntuforums.org/showthread.php?t=808543)

I however found this thread. Ubuntu 11.10 uses lightdm. While there is no lightdm in that file he is describing... Maybe that is the issue preventing to shut down?

Is there a way for me to find out what exactly is going wrong? a log file I could explore?

What are the specifications for your computer?

You could edit the /etc/default/grub file and remove the "quiet" from the line ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
``` so that it will print out text when your system starts and stops.You then have to run ```
sudo update-grub
``` to update the boot file so the text appears during the boot and shutdown phases.

You could also try to add "acpi=force" to the same file to see if it might be an acpi problem.

Good Luck

---

### Post by jerrrys on 2012-03-19
maybe

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/869635](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/869635)

---

