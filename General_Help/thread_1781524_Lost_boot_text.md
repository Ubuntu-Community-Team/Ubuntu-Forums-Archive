---
title: "Lost boot text"
date: 2011-06-13
forum: General Help
---

### Post by doctordruidphd on 2011-06-13
Beginning with Maverick, I no longer get text on the screen while booting. I do not use Plymouth, and have removed its entries from /etc/init.d and its hooks from /usr/share/initramfs-tools/hooks (and run update-initramfs -u). I have set up /etc/default/grub so that there are no "quiet" or "splash" entries, and I have tried it both with and without the "text" in the GRUB_CMDLINE_LINUX_DEFAULT="text" line (and having run update-grub)

What happens is that after choosing the boot item in the grub menu, the screen goes black, and stays that way until after the fsck lines, then the text appears. I would really like to see the full text from the beginning of the kernel boot, instead of just a black screen.

I have tried this with the vesa video driver, nouveau, and nvidia-current from the xswat repository, same results. And this happens in maverick, natty, and oneiric.

Anyone else have this problem, and is there a solution?

Thanks.

---

