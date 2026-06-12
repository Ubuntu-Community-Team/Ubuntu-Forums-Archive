---
title: "Resize swap partition??"
date: 2010-05-27
forum: General Help
---

### Post by Kaneda187 on 2010-05-27
Hey people! 

Can anyone out..... ====> tell me the best way to resize a swap partition? 

I read somewhere that your swap partition should be the same size as you RAM in order for Suspend to work.....?

Im running Lucid

Thanks in advance

---

### Post by jerenept on 2010-05-27
Use the live CD. It comes with GParted, a graphical disk partitioning utility. 
System>Administration>Gparted Partition Editor
or <alt+f2> type ```
sudo gparted
``` and press enter
Edit your partitions there.

---

### Post by lmarmisa on 2010-05-27
GParted is a good tool for that purpose.

But this task is not trivial. When you modify the size of a swap partition, you change its UUID. So, you will have to update the /etc/fstab with the new UUID of your swap partition.

Theses bash commands could be useful if you try to change the size of your swap partition:

> 
#List the UUIDs detected in your system
sudo blkid

# Stop the swap
sudo swapoff -a

#Restart the swap
sudo swapon -a



Best regards,

Luis

---

### Post by lmarmisa on 2010-05-27
You can use an Ubuntu Live CD, but I think that it is easier to run your Lucid Ubuntu.

GParted is not included in the standard Ubuntu installation. So, please, install it using Synaptic.

---

### Post by sdennie on 2010-05-27
You actually don't need any swap at all for suspend.  You do need it for hibernate though.  You may want to read through the Ubuntu Swap FAQ and decide if you really need more swap: [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by Kaneda187 on 2010-05-27
so is there any other reason my suspend or hibernate dont work?

---

### Post by dcstar on 2010-05-27
> **Kaneda187 said:**
> so is there any other reason my suspend or hibernate dont work?

My PC would not Suspend when my Swap was too small, as soon as I resized it (and fixed the UUID in the resume file) it would Suspend and Hibernate correctly.

Try it.

---

### Post by sdennie on 2010-05-27
> **dcstar said:**
> My PC would not Suspend when my Swap was too small, as soon as I resized it (and fixed the UUID in the resume file) it would Suspend and Hibernate correctly.

Try it.

That sounds like a completely separate issue.  I've been running without any swap at all on this laptop for 2 years and it has suspend and resumed without fail every day.

---

### Post by lmarmisa on 2010-05-27
You can read this interesting comment in this page: [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

[INDENT]*Hibernation (suspend-to-disk) The hibernation feature  (suspend-to-disk) writes out the contents of RAM to the swap partition  before turning off the machine. Therefore, your swap partition should be  at least as big as your RAM size. The hibernation implementation  currently used in Ubuntu, swsusp, needs a swap or suspend partition. It  cannot use a swap file on an active file system. *
[/INDENT]

---

### Post by Kaneda187 on 2010-05-28
I think I'll give it a try later!

thanks and let ya know how it goes!

---

