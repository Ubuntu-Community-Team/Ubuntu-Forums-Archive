---
title: "How do I partition my ubuntu drive"
date: 2009-10-01
forum: General Help
---

### Post by iFuzo on 2009-10-01
How can I partition it to NTFS so I can install windows.

My ubuntu experience was great just it no longer has a use to me

---

### Post by iFuzo on 2009-10-01
PS: Dont offer the option of install in vmware of virtualbox please

---

### Post by akakingess on 2009-10-01
I would just put in your Ubuntu Live CD and run Gparted and choose to reformat the whole disk to Fat or NTFS and then restart and put in your Windows CD which should see the disk at that point.

---

### Post by scouser73 on 2009-10-01
Install Gparted from the Synaptic Package Manager, once installed you can find it under **System > Administration > Partition Editor**.

---

### Post by AndyCee on 2009-10-01
> **iFuzo said:**
> How can I partition it to NTFS so I can install windows.

My ubuntu experience was great just it no longer has a use to me

If you're planning to blow away your Ubuntu install, you should be able to pop in the Windows install DVD and it will reformat the disk to NTFS for you.

---

### Post by iFuzo on 2009-10-01
I cant format it using windows live cd, I get "Failed to format the selected partition [Error:0x80004005]"

---

### Post by iFuzo on 2009-10-01
UPDATE: I cant use gparted, It wont let me unmount

---

### Post by qamelian on 2009-10-01
> **iFuzo said:**
> UPDATE: I cant use gparted, It wont let me unmount
You need to be running it from the LiveCD. You can't unmount a partition that is in use, which will be the case if you're booting from the hard drive.

---

