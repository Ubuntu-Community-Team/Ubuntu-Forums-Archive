---
title: "Multiple Kernel (Fail Safe)"
date: 2011-03-24
forum: General Help
---

### Post by bpushia on 2011-03-24
How do I install an additional kernel in Linux Ubuntu 10.10, in case of a boot failure? Also how do I make the Grub Menu Visible, so that I am able to select multiple kernels. There is an older solution below, but is there a way to do this in Linux Ubuntu 10.10. I just suffered an update failure, possibly due to a corrupt kernel upgrade, which made my system unbootable. The cursor just flashed continuously. 

-----------------------------------------------------------------

Solution of 2007
found- [http://www.zdnet.co.uk/news/it-at-work/2007/08/01/rescuing-linux-when-it-wont-start-39288346/](http://www.zdnet.co.uk/news/it-at-work/2007/08/01/rescuing-linux-when-it-wont-start-39288346/)

"The next obvious rescue aid is to always have a working kernel installed. I usually work from a kernel updated via yum. Kernels have occasionally been released with flaws that have caused one or more of my machines to not boot. To this end, I always make sure I have at least one perfectly running kernel on a machine. A great way to handle this is to first add plugins=1 in your /etc/yum.conf file. The next step is to take this script (written by Jeremy Katz from Red Hat) and save it as n-installonly.py in /usr/lib/yum-plugins. You can change the number of kernels to retain on the system by changing the tookeep variable (default = 2).

With a known working kernel on your system, you can upgrade safely. If the new kernel is hosed, simply boot the old kernel to solve the issue with the new kernel — be it to remove it, recompile it, or update it."

---

### Post by cherva on 2011-03-24
I think to show up the grub menu you have to boot your PC and hold the left shift key.

---

### Post by JKyleOKC on 2011-03-24
The left shift key works for me.

If you've just installed 10.10, and have only one kernel version listed on the menu when you see it, you really have no need for any older version. When a newer version becomes available through the update route, your older one will remain installed, so as time passes you'll have the backups available. Right now, I'm using the previous kernel on this box because the newest one doesn't want to see my local network.

However, if you'll feel safer having a fallback, you can open the Synaptic package manager from the system menu, and search for "linux-kernel" to see what's available. The ones you have installed will have their check boxes filled in green, on the display, while the rest will have the check boxes blank. Select the one that's a single version older than your oldest "installed" one and click its check box, then select "mark for installation" and follow the prompts. Finally, check "Apply" to download and install your selection. The grub menu will automatically get updated to reflect it.

---

### Post by bpushia on 2011-03-24
Ok

This solves my problem. I do believe I will feel much safer with an older kernel listed. I really do not like having to reinstall Linux due to a kernel mishap. 

Thanks allot cherva, and JKyleOKC. ;)

---

