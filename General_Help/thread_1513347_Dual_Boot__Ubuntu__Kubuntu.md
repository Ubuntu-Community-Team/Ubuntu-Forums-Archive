---
title: "Dual Boot:  Ubuntu / Kubuntu"
date: 2010-06-19
forum: General Help
---

### Post by paulmguest on 2010-06-19
Hi everybody,

I'm still learning the finer points of Linux.  I have a question about partitions -  I dual boot with both Ubunbtu and Kubuntu.  I'd like to remove my Kubuntu partition, but I don't feel I know enough to comfortably go ahead.

How exactly do you correctly identify which is which?

Paul

---

### Post by cj.surrusco on 2010-06-19
Boot into Ubuntu, and open the fstab.
```
sudo gedit /etc/fstab
```

Look at the line that has the mount point "/". That is your root partition for Ubuntu. Take down the UUID on that line.

Open GParted, and locate the partition that does **NOT** have the UUID that you see in the "/" line of the fstab. That is your Kubuntu partition and you then can delete it.

---

### Post by WorMzy on 2010-06-19
Be careful when deleting partitions. If you delete the partition which is used by grub during the boot process, then you will need to reinstall grub to your other partition before you'll be able to boot again.

---

### Post by oldfred on 2010-06-19
I run this for my own info, even though it is set up to help debug boot issues. It will tell you what partitions are what and which is in the MBR for booting.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.

---

### Post by cj.surrusco on 2010-06-19
> **WorMzy said:**
> Be careful when deleting partitions. If you delete the partition which is used during by grub during the boot process, then you will need to reinstall grub to your other partition before you'll be able to boot again.

Good point. It would be a good idea to reinstall grub before removing the partitions. First, you need to know which grub version you have.

```
grub-install -v
```

EDIT: oldfred's approach will be much easier to follow.

---

