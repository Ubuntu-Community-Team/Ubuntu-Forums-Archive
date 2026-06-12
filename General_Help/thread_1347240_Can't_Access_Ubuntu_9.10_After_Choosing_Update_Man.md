---
title: "Can't Access Ubuntu 9.10 After Choosing Update Manager"
date: 2009-12-06
forum: General Help
---

### Post by Richiegs on 2009-12-06
I have been  using Ubuntu 9.10 for a few weeks. I just chose to Update Manager to get the latest files and restarted the computer. As a result, I am no longer able to access Ubuntu. The message read: Kernel panic: unable to mount root fs on unknown block. Does anyone please tell me what the problem is and how to fix it? Is it possible to reverse or undone what I just updated before this? Thank you very much

---

### Post by akakingess on 2009-12-06
When Grub list is up during booting, choose the previous Kernel and see if it comes up that way.

---

### Post by Richiegs on 2009-12-06
> **akakingess said:**
> When Grub list is up during booting, choose the previous Kernel and see if it comes up that way.
  I am able to access Ubuntu 2.6.31-15, but not Ubuntu 2.6.31-16.
What is the difference between them? Can i reverse the update process?

---

### Post by akakingess on 2009-12-06
> **Richiegs said:**
> I am able to access Ubuntu 2.6.31-15, but not Ubuntu 2.6.31-16.
What is the difference between them? Can i reverse the update process?
You can just uninstall the -16 kernel version within synaptic package manager, or just change the default in your grub.list to the -15, or just wait for the next kernel update. As you can tell, there are several options here, just don't use -16 for now, or uninstall it, but when you do the Update Manager, it may want to upgrade the kernel again so you may have to deselect it until an even newer version of the kernel comes out.

By The Way: You can do a "man grub" to view the grub manual and learn more about it...

---

### Post by Richiegs on 2009-12-06
[quote=akakingess;8448642]You can just uninstall the -16 kernel version within synaptic package manager, HOW to uninstall it?
?
or just change the default in your grub.list to the -15, HOW to set it to default?

Thank you

---

### Post by wilee-nilee on 2009-12-06
You can install startup manager from synaptic and it will allow a default kernel.

---

