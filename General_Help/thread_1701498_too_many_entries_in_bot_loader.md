---
title: "too many entries in bot loader"
date: 2011-03-06
forum: General Help
---

### Post by vat with tux on 2011-03-06
Whenever i updates ubuntu through update manager at the next boot i found two more entries (one of which is for recovery mode) added in my boot menu. So can anyone tell why it is so? And how to get rid of it.:)
Thanking in advance.

---

### Post by mcduck on 2011-03-06
When you get a kernel update, the new kernel version doesn't replace the old one, but is installed alongside it instead. This way you can test the new version to make sure it works for you, while still having the old version available if you have problems with the new one.

When you are sure everything is working fine on your system with the new kernel, you can simply uninstall the old one's packages and the menu entries will be removed automatically.

The easiest way to uninstall old kernels is the Computer Janitor, in the System/Administration-menu. But be careful with what you let it uninstall, some people have had problems with it removing packages they actually want to keep.

Another option is to just do it manually, using te Synaptic Package Manager. Find the linux-image and linux-headers -packages for the old kernel version and uninstall them. Make sure you don't remove the kenrel you are actually using, of course.

---

### Post by Timmer1240 on 2011-03-06
To remove all the unused Linux Kernel headers, images and modules, simply run this command: dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | xargs sudo apt-get -y purge

---

### Post by vat with tux on 2011-03-08
> **mcduck said:**
> When you get a kernel update, the new kernel version doesn't replace the old one, but is installed alongside it instead. This way you can test the new version to make sure it works for you, while still having the old version available if you have problems with the new one.

When you are sure everything is working fine on your system with the new kernel, you can simply uninstall the old one's packages and the menu entries will be removed automatically.

The easiest way to uninstall old kernels is the Computer Janitor, in the System/Administration-menu. But be careful with what you let it uninstall, some people have had problems with it removing packages they actually want to keep.

Another option is to just do it manually, using te Synaptic Package Manager. Find the linux-image and linux-headers -packages for the old kernel version and uninstall them. Make sure you don't remove the kenrel you are actually using, of course.

When i opened computer janitor it shows one message telling "There is nothing to clean up". what to do next?

---

### Post by mcduck on 2011-03-08
> **vat with tux said:**
> When i opened computer janitor it shows one message telling "There is nothing to clean up". what to do next?

Then use the manual method with Synaptic Package Manager, like I described in my previous post.

---

### Post by wormyblackburny on 2011-03-08
Open a terminal and type uname -r to find out which kernel you are running, then use synaptic to remove the old kernels. When you are done, run sudo update-grub to update the list of available kernels

---

