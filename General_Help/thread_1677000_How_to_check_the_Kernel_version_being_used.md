---
title: "How to check the Kernel version being used"
date: 2011-01-28
forum: General Help
---

### Post by raunhar on 2011-01-28
Ubuntu version 10.10
Today downloaded the upgrades, where it showed Linux header Kernel of a new version.
On reboot, the GRUB showed showed the same old version (2.6.35-22-generic) before upgrade.

how do I check, if the kernel has been upgraded or not.

---

### Post by robert shearer on 2011-01-28
in a terminal type...
```
uname -a
```

that will show the **running** kernel

to see the kernels installed open synaptic and search for 'linux-image'.
That should show the installed ones.

If grub is not showing the most recent you may have to, in a terminal, run
```
sudo update-grub
```

If that does not fix it then consider reinstalling grub.
open synaptic and find 'grub-pc ' mark it for re-installation and apply.
Then run ```
sudo update-grub
``` again and reboot.
Fixed it for me.

---

### Post by raunhar on 2011-01-28
It shows 2.6.35-22 genric
Grub version is Grub 0.97

I need to keep this version as I can edit the menu.lst file to display selected list on boot.

---

### Post by robert shearer on 2011-01-28
> **raunhar said:**
> It shows 2.6.35-22 genric

That is the running ??
Whats the installed ??

> Grub version is Grub 0.97

I need to keep this version as I can edit the menu.lst file to display selected list on boot.

So edit menu.lst and add the new kernel.

---

### Post by raunhar on 2011-01-28
uname -a also shows the same version.
But Upgrade Manager showed a different version being downloaded.

---

### Post by robert shearer on 2011-01-28
After today's update I have 2.6.35-25-generic.

Open Synaptic>File>History and check through to see for sure that a newer kernel has been downloaded.
EDIT no that doesn't seem to work anymore. Well not showing here.

When you checked Synaptic for installed kernels (search term = linux-image) did you scroll right down through the results looking for the newest. There will be several listed.

---

### Post by raunhar on 2011-01-28
The History shows nothing after Nov. 2010.

Although I am updating regularly.

---

### Post by robert shearer on 2011-01-28
> **raunhar said:**
> The History shows nothing after Nov. 2010.

Although I am updating regularly.

Yeah, it used to show everything but now it seems it shows only things you have installed/uninstalled directly with Synaptic.

Check my edit in my previous post.

---

### Post by robert shearer on 2011-01-28
Can you run...
```
dpkg --list | grep linux-image
```
and post the output.

---

### Post by raunhar on 2011-01-28
list | grep linux-image
rc  linux-image-2.6.28-11-generic              2.6.28-11.42                                        Linux kernel image for version 2.6.28 on x86/x86_64
ii  linux-image-2.6.28-19-generic              2.6.28-19.66                                        Linux kernel image for version 2.6.28 on x86/x86_64
ii  linux-image-2.6.31-22-generic              2.6.31-22.67                                        Linux kernel image for version 2.6.31 on x86/x86_64
ii  linux-image-2.6.32-25-generic              2.6.32-25.45                                        Linux kernel image for version 2.6.32 on x86/x86_64
ii  linux-image-2.6.35-22-generic              2.6.35-22.35                                        Linux kernel image for version 2.6.35 on x86/x86_64
ii  linux-image-2.6.35-23-generic              2.6.35-23.41                                        Linux kernel image for version 2.6.35 on x86/x86_64
ii  linux-image-2.6.35-24-generic              2.6.35-24.42                                        Linux kernel image for version 2.6.35 on x86/x86_64
ii  linux-image-2.6.35-25-generic              2.6.35-25.44                                        Linux kernel image for version 2.6.35 on x86/x86_64
ii  linux-image-generic                        2.6.35.25.32                                        Generic Linux kernel image

---

### Post by robert shearer on 2011-01-28
> **raunhar said:**
> list | grep linux-image
rc  linux-image-2.6.28-11-generic              2.6.28-11.42                                        Linux kernel image for version 2.6.28 on x86/x86_64
ii  linux-image-2.6.28-19-generic              2.6.28-19.66                                        Linux kernel image for version 2.6.28 on x86/x86_64
ii  linux-image-2.6.31-22-generic              2.6.31-22.67                                        Linux kernel image for version 2.6.31 on x86/x86_64
ii  linux-image-2.6.32-25-generic              2.6.32-25.45                                        Linux kernel image for version 2.6.32 on x86/x86_64
ii  linux-image-2.6.35-22-generic              2.6.35-22.35                                        Linux kernel image for version 2.6.35 on x86/x86_64
ii  linux-image-2.6.35-23-generic              2.6.35-23.41                                        Linux kernel image for version 2.6.35 on x86/x86_64
ii  linux-image-2.6.35-24-generic              2.6.35-24.42                                        Linux kernel image for version 2.6.35 on x86/x86_64
**ii  linux-image-2.6.35-25-generic              2.6.35-25.44                                        Linux kernel image for version 2.6.35 on x86/x86_64**
ii  linux-image-generic                        2.6.35.25.32                                        Generic Linux kernel image

It is there so you should be able to edit menu.lst and add it.

You have a lot of old kernels there so if you don't need or use them go into Synaptic and remove some of the older ones.
Usually you only need the latest and the previous as a fall-back though I like to keep another as well. Note always keep the linux-image-generic(last one on your list) So keep 23,24,25,and generic ie last 4 on your list.

Wonder if grub is only showing a set number of kernels (5 ?)and removing some may allow it to show the newer ones ??  Don't know.

With that many kernels in the grub menu you would have to scroll up and down the grub screen to see them all, were you aware of that ?

---

