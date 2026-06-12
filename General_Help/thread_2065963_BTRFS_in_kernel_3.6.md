---
title: "BTRFS in kernel 3.6"
date: 2012-10-03
forum: General Help
---

### Post by joiseystud on 2012-10-03
Now that BTRFS has received some udpates in the new 3.6 Kernel, what do I have to do to take advantage of them? I installed my Btrfs using the 3.2.x kernel that comes in 12.04.1 Ubuntu.  Not sure if it upgrades automatically at mount time on the new kernel, or is it something where I need to run a command?

---

### Post by 2F4U on 2012-10-03
> Not sure if it upgrades automatically at mount time on the new kernel, or is it something where I need to run a command?

New kernel are only installed through software upgrades, but it is unlikely that you will ever get kernel 3.6 with Ubuntu 12.04.

---

### Post by joiseystud on 2012-10-03
> **2F4U said:**
> New kernel are only installed through software upgrades, but it is unlikely that you will ever get kernel 3.6 with Ubuntu 12.04.

Actually I am running the 3.6 Kernel on 12.04. Its actually not hard. 

You go to [Ubuntu Kernel Mainline PPA for 3.60]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6-quantal/")

You download the x86 or x64 packages depending on what you want to run, plus the *_all.deb into the same folder (I use downloads).  I then open a terminal, navigate to the Downloads folder. 

Then type:
```
sudo dpkg -i linux*
```

From there the new kernel will install and grub will be updated.  You reboot and your new default kernel is 3.6.  If you want another you can always select an older kernel from the grub menu.

---

### Post by ssam on 2012-10-04
most of the BTRFS improvements come just from running the new kernel. some of them must be enabled with mount options ( [https://btrfs.wiki.kernel.org/index.php/Mount_options](https://btrfs.wiki.kernel.org/index.php/Mount_options) )

Some things like send and receive, and quotas, will need a new version of btrfs-progs to use. figuring out which version of btrfs-progs can be hard because most distros ship a git version between 0.19 and 0.20. from the [https://launchpad.net/ubuntu/+source/btrfs-tools](https://launchpad.net/ubuntu/+source/btrfs-tools) it looks like 12.04 ships a 2 year old snapshot, which will lack many features. so you might want to compile a newer snapshot from git, or find one in a PPA.

---

