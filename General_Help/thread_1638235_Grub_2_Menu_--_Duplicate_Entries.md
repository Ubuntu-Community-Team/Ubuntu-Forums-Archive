---
title: "Grub 2 Menu -- Duplicate Entries"
date: 2010-12-05
forum: General Help
---

### Post by Sunrock on 2010-12-05
For the past few weeks I have been using the lastest Ubuntu OS.  The following menu pops-up during the boot process.


GNU GRUB version 1.98+20100804-5ubuntu3

Ubuntu, with Linux 2.6.35-22-generic-pae
Ubuntu, with Linux 2.6.35-22-generic-pae (recovery mode)
Memory test (mentest86+)
Memory test (mentest86+, serial console 115200)
Windows 7 (loader) (on /dev/sdb1) 

Just recently the menu displays duplicate entries.  The first two entries are repeated (see below). Can anyone tell me what might have caused these duplicate entries to appear and how to correct them?  Before this problem occurred I did not issue any sudo commands.


GNU GRUB version 1.98+20100804-5ubuntu3

Ubuntu, with Linux 2.6.35-22-generic-pae
Ubuntu, with Linux 2.6.35-22-generic-pae (recovery mode)
Ubuntu, with Linux 2.6.35-22-generic-pae
Ubuntu, with Linux 2.6.35-22-generic-pae (recovery mode)
Memory test (mentest86+)
Memory test (mentest86+, serial console 115200)
Windows 7 (loader) (on /dev/sdb1) 


Sunrock

---

### Post by Verbeck on 2010-12-05
are you sure the numbers are the same?
if the kernel gets updated, it wont remove the older one automatically and will be displayed there

else, run *sudo update-grub *from a terminal

---

### Post by Sunrock on 2010-12-05
After I read your reply, I rebooted and I found the first two lines different from the next two lines by one number.  The first two lines have a “-23” before the word generic while the next two lines have a “-22.”  Yes, I did run “sudo update-grub” from a terminal before I posted my problem. Any other suggestions?

GNU GRUB version 1.98+20100804-5ubuntu3

Ubuntu, with Linux 2.6.35-23-generic-pae
Ubuntu, with Linux 2.6.35-23-generic-pae (recovery mode)
Ubuntu, with Linux 2.6.35-22-generic-pae
Ubuntu, with Linux 2.6.35-22-generic-pae (recovery mode)
Memory test (mentest86+)
Memory test (mentest86+, serial console 115200)
Windows 7 (loader) (on /dev/sdb1) 


Sunrock

---

### Post by wilee-nilee on 2010-12-05
> **Sunrock said:**
> After I read your reply, I rebooted and I found the first two lines different from the next two lines by one number.  The first two lines have a “-23” before the word generic while the next two lines have a “-22.”  Yes, I did run “sudo update-grub” from a terminal before I posted my problem. Any other suggestions?

GNU GRUB version 1.98+20100804-5ubuntu3

Ubuntu, with Linux 2.6.35-23-generic-pae
Ubuntu, with Linux 2.6.35-23-generic-pae (recovery mode)
Ubuntu, with Linux 2.6.35-22-generic-pae
Ubuntu, with Linux 2.6.35-22-generic-pae (recovery mode)
Memory test (mentest86+)
Memory test (mentest86+, serial console 115200)
Windows 7 (loader) (on /dev/sdb1) 


Sunrock

That is completely normal, it is advised to have 2 sets of kernels in case there is a problem with one you have the other. The kernels take up very little space on the HD so keeping both sets is a insurance policy so to speak.

If your new to this whole thing just learn and use the system a little more before trying to have the customized set up you may desire.

---

### Post by Verbeck on 2010-12-05
its good practice to have the older kernel around for some time, 

but if you dont want it, you can remove the older one from synaptic (system>administration>synaptic package manager)
search for 'linux-image' and remove the version 2.6.35-22

after that, run *sudo update-grub *again

---

### Post by Sunrock on 2010-12-05
Thanks for your responses.  Now, I understand a little more how the Grub Menu works.  For now, I will leave the backup kernel lines.

Sunrock

---

