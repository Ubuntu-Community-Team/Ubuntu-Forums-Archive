---
title: "Removing Kernel"
date: 2010-09-04
forum: General Help
---

### Post by satish_j on 2010-09-04
My Grub Menus shows 2.6.32.24 and 2.6.32.21 kernels at startup.THrough synaptic,i removed 2.6.32.21 and rebooted the system.
I expected Grub to show only one kernel this time,but it kept showing same 2 options and i was even able to login to the kernel that was removed from synaptic..
Any ideas how to remove the deleted kernel from Grub options??

---

### Post by mendhak on 2010-09-04
Did you run a 

sudo update-grub

after removing the kernels?

---

### Post by mendhak on 2010-09-04
Also, when I've removed a kernel in the past, I've gone to Synaptic and removed

linux-headers-2.x.x-x
linux-headers-2.x.x-x-generic
linux-image-2.x.x-x-generic

So that's three entries.

---

### Post by drs305 on 2010-09-04
If you are still using 8.04 you can install "startupmanager" and use it to select the number of kernels to display. You can set it to one to hide the older kernel (or the number you want to display, assuming the one you want to remove is the oldest).

For removing old kernels, an easy way is to use ubuntu-tweak. I believe it's in the Software Center on new releases. You can add it by visiting this site for older releases:
[https://launchpad.net/ubuntu-tweak/+download]("https://launchpad.net/ubuntu-tweak/+download")

For later Ubuntu releases, you can add the repository if it's not in the Software Center:
[http://ubuntu-tweak.com/downloads/]("http://ubuntu-tweak.com/downloads/")

---

### Post by satish_j on 2010-09-04
> **mendhak said:**
> Also, when I've removed a kernel in the past, I've gone to Synaptic and removed

linux-headers-2.x.x-x
linux-headers-2.x.x-x-generic
linux-image-2.x.x-x-generic

So that's three entries.

Well, i selected linux-headers-2.6.32-21 and seleceted COMPLETE REMOVAL and assumed it will handle all the dependencies,but,now synaptic still shows me linux-image-2.6.32-21..
Proceeding with emoving the same and will update the same..:)

---

### Post by satish_j on 2010-09-04
solved after removing the image file..
thanks for the help..

---

### Post by mendhak on 2010-09-04
That's good, but don't forget Ubuntu Tweak, it's extremely useful.  I should've mentioned it first :D

---

### Post by scouser73 on 2010-09-04
> **mendhak said:**
> That's good, but don't forget Ubuntu Tweak, it's extremely useful.  I should've mentioned it first :D

+1 for Ubuntu Tweak to remove old Kernels.

---

