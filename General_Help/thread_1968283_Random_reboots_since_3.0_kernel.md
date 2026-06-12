---
title: "Random reboots since 3.0 kernel"
date: 2012-04-28
forum: General Help
---

### Post by baokeyai on 2012-04-28
I have an Ubuntu Server that is now upgraded to 12.04 LTS server. Ever since I've upgraded from 10.10 to 11.04, when the kernel went from 2.6.38 to 3.0.anything, my machine would constantly randomly reboot about 2-3 minutes in. 
 
Whether it was idle or if I did anything it would just randomly reboot.
 
Now if I chose the old kernel of 2.6.38 in 11.04 or 11.10 or event 12.04, it would be rock solid and have no complaints. However, if I performed any update that required a reboot, I would always test if the new kernel version would fix whatever was causing the random reboots.
 
Now that it upgraded to 12.04 and the 3.2 kernel, I was really hoping that all would have been resolved, but to my disappointment, it's still doing the random reboots. 
 
However, I think that 12.04 has a new feature that is providing a clue to the root cause. I got a screen to report the error as it report that the "colord" daemon caused a crash with the SIGSEGV message.
 
So this is a longshot if anyone has had the same problem cause I've googled this thing for the past year to no avail. I hate to rebuild the box for the sake of rebuilding the box, since all I have to do is go back to 2.6 kernel and all works well. 
 
Appreciate any input!
 
[Actual Cause]
I had many kernels installed on my machine, Generic/Server and various old versions.
 
[Solution]
Removed all kernels, re-installed just one linux-server kernel and everything works fine now

---

### Post by xyzzyman on 2012-04-28
Have you even installed a 3.0 'mainline' kernel [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) ?

That way you can root out if it's an ubuntu sauce patch changing something, or upstream with the mainline kernel.

---

### Post by baokeyai on 2012-04-29
is there an easymode way to do this through synaptics? Or should I just copy the kernel in to the /boot folder?

---

### Post by CharlesA on 2012-04-29
> **baokeyai said:**
> is there an easymode way to do this through synaptics? Or should I just copy the kernel in to the /boot folder?

For installing a mainline kernel? No easy way that I know of.

Have you checked /var/log/messages or dmesg to see if there are any errors prior to reboot?

---

### Post by baokeyai on 2012-04-30
all seems well in the dmesg and then all of a sudden it reboots.
 
I wish I could give you guys more, but maybe it will just require a clean full rebuild :(

---

### Post by xyzzyman on 2012-04-30
Download the two headers and the kernel image from the link I gave, then install the DEB's.

---

### Post by baokeyai on 2012-05-01
Installed the headers and image from the following
 
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.2.16-precise/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.2.16-precise/)
 
installed all the Debs, but resulted in the same random reboot scenario :(
 
Install wasn't that difficult, but alas no dice.
 
Any other ideas?

---

### Post by CharlesA on 2012-05-01
File a bug report.

---

### Post by baokeyai on 2012-06-11
Just wanted to mentioned that I resolved the problem for anyone who may encounter the same

---

### Post by CharlesA on 2012-06-11
> **baokeyai said:**
> Just wanted to mentioned that I resolved the problem for anyone who may encounter the same

Kinda odd that uninstalling all the kernels and only installing the current one fixed the problem.

Glad you got it sorted in any case. :)

---

