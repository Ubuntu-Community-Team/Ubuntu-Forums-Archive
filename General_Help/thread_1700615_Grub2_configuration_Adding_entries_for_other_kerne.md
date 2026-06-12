---
title: "Grub2 configuration: Adding entries for other kernels"
date: 2011-03-05
forum: General Help
---

### Post by Roaring Silence on 2011-03-05
Is it possible to add menu entries for older kernels to boot instead of the latest?
I have tried this in Ubuntu 10.04 and it hasn't worked.
This used to be possible with ease in grub legacy.
I copied the current menu entry from /boot/grub/grub.cfg and pasted it in the /etc/grub.d/ 20_custom file.
Then I changed the kernel number to the older kernel number and the initrd number too. 
#update-grub puts this entry into 'grub.cfg', but it doesn't work.
I get:
"Error file not found    and
 Error: You need to load the kernel first"
What is wrong?
The old kernel is in /boot as well as the respective initrd and config files.
Any help would be appreciated, thanks.

---

### Post by Roaring Silence on 2011-03-05
Yes it is.
I have found my error. I had prefixed the linux and initrd entries with /boot, which isn't required.
I wish we could just be allowed to edit the grub.cfg file directly, instead of configuring with several other files. Seems unnecessarily complicated.

---

