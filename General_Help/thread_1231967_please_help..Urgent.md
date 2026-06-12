---
title: "please help..Urgent"
date: 2009-08-05
forum: General Help
---

### Post by srinivas2828 on 2009-08-05
Hi friends
recently i have installed VirtualBox into my Ubuntu 8.04 machine  and again i installed ubuntu 8.04 into virtualbox and i installed some packeges into that,Now what i want is i want to clone the HardDisk and i want to make it as bootable..does anybosy have idea about that

---

### Post by nhanquy on 2009-08-05
want to clone/copy ubuntu from one disk to another?

A.[INDENT]1.Use gparted to format the new disk (or fdisk or sfidk,...) I prefer gparted  )Partition Editor in Linux)
  create linux partition as well swap partition. Thay need not to be the same size with src.
2. Boot from a liveCD (or USB drive) not from hard drive you want to clone!
3. Use tar to copy over:
  tar cf - -C /media/src . | tar xvf - -C /media/dst
(of course you have mounted src and dst to /media/src and /media/dst...)
4. run grub on the new disk to transfer boot code ( find /boot/grub/stage1 ...)
5.. fix /etc/fstab and /boot/grub/menu.lst on the dst (change to have correct UUID)

Those are for two disks with different size or different partition size.
[/INDENT]B.[INDENT]If the two disks are identical. Then just use dd like:

dd if=/dev/sda of=dev/sdb

{after booting from the liveCD or USB drive)
[/INDENT]

---

### Post by srinivas2828 on 2009-08-05
thanks for your reply But i want to clone guest operating system from virtualbox to host machine

---

### Post by nhanquy on 2009-08-05
That's strange real strange!
Why don't you just install packages to the host. But the host is already linux why do you need it again in the virtual box?
I guess you can copy over the conifg (from the virtual box) after installing to the host to have them identical.

---

### Post by barnex on 2009-08-05
You can export a list of installed packages like this (on the virtural system)

```
dpkg --get-selections > selections.txt
```

then move selections.txt to the new machine and run:

```

dpkg --set-selections < selections.txt
apt-get update
apt-get upgrade

```

In this way you will obtain more or less a "clone" of your virtual system

---

### Post by infinitejones on 2009-08-05
I think the OP has set up a test environment in Virtualbox, to make sure that Ubuntu 8.04 doesn't have problems during/after installing various packages. Now that he/she has confirmed that everything works in the test environment with Virtualbox, he/she wants to replicate that environment on the actual host.

In other words, he/she wants to convert a virtualbox image into an actual hard-drive image. 

No idea how to do that, or even if it would work... however what I can suggest is asking Synaptic to produce a list of installed applications in the virtualbox environment, setting up a shared folder between the virtual OS and the host, and then loading list into Synaptic on the host and letting Synaptic do its stuff.

In the virtual OS, open Synaptic, click File, then Save Markings As... Give it a name, make sure "Save full state, not only changes" is ticked, and save it into a folder shared between the virtual OS and the host.

Then open Synaptic on the host, click file, and then Load Markings.

Obviously you'll also need to make sure the /etc/apt/sources.list file contain the same repositories on the virtual OS and the host.

---

### Post by infinitejones on 2009-08-05
> **infinitejones said:**
> I think the OP has set up a test environment in Virtualbox, to make sure that Ubuntu 8.04 doesn't have problems during/after installing various packages. Now that he/she has confirmed that everything works in the test environment with Virtualbox, he/she wants to replicate that environment on the actual host.

In other words, he/she wants to convert a virtualbox image into an actual hard-drive image. 

No idea how to do that, or even if it would work... however what I can suggest is asking Synaptic to produce a list of installed applications in the virtualbox environment, setting up a shared folder between the virtual OS and the host, and then loading list into Synaptic on the host and letting Synaptic do its stuff.

In the virtual OS, open Synaptic, click File, then Save Markings As... Give it a name, make sure "Save full state, not only changes" is ticked, and save it into a folder shared between the virtual OS and the host.

Then open Synaptic on the host, click file, and then Load Markings.

Obviously you'll also need to make sure the /etc/apt/sources.list file contain the same repositories on the virtual OS and the host.

Or do it the easy way, like the post above mine!

---

