---
title: "grub2 cannot delete a kernel entry"
date: 2010-12-13
forum: General Help
---

### Post by Oldhacker on 2010-12-13
After searching through the forums, I tried every method that I could find to delete an old kernel entry from grub2. That included Synaptic Package Manager, Grub Customizer, etc. but even after removing the two entries for that kernel with Synaptic Package Manager the entry still remains in grub2 menu whenever I boot. It is not a great problem, but it is frustrating to find a file that resists all attempts at change.

---

### Post by coffeecat on 2010-12-13
When you uninstall an old kernel using Synaptic package manager, it should run update-grub automatically and if the kernel has indeed been fully uninstalled then the menu entry for that particular kernel will disappear. Which makes me think you may not have uninstalled all the relevant kernel packages. Depending on the release version of Ubuntu you are running there will be three or four packages making up a particular version of the kernel. 

I suggest you search Synaptic again. If the kernel was, say, version 2.6.32-12, then use the string "2.6.32-12" in your search. See if there are any packages still installed matching/containing that string.

If all else fails, run this from the terminal:

```
sudo update-grub
```

---

### Post by garvinrick4 on 2010-12-13
#This code will give you your grub menu entries so you
do not have to reboot to check.

```
grep menuentry /boot/grub/grub.cfg
```
##If you have more than one linux install make sure you 
update-grub on one that is your first in boot order.

---

### Post by Oldhacker on 2010-12-13
The replies that you gave were the answer to my puzzle. There WAS another Linux kernel file present with the same number. Once that was deleted and I did the sudo update-grub (which I did before without locating the additional file) my grub menu was corrected.

Thank you for your knowledgeable assistance.

---

