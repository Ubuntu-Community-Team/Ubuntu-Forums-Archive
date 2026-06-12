---
title: "Kubuntu 9.04: How do I access my Fedora HD?"
date: 2009-10-20
forum: General Help
---

### Post by Gandalf_the_Grey on 2009-10-20
I have Kubuntu 9.04 on my seondary master hard drive, with Fedora on my primary master. Recently, I accidentally messed up my Fedora install by mucking up the video driver.  Now, I have no access to Fedora except through rescue mode.  Kubuntu can't see the Fedora hard disk, or at least it doesn't appear under Dolphin.  How can I get my important files transferred to Ubuntu so I can reinstall Fedora without losing anything?  I do have access to a Fedora Live CD, but that can't see the Kubuntu install drive.

---

### Post by Giblet5 on 2009-10-20
What partition is Fedora on? /dev/sda1? Then this will mount it:
```
sudo mount /dev/sda1 /mnt -text3
```

If you aren't sure, this will tell you where it is: ```
sudo fdisk -l
```

Mount it and you can see it with a gui browser.

If you're gonna do work in Fedora and Ubuntu on the same box, you'll benefit from learning to use the command line.

Modern linux installs have some semi-useful gui interfaces, but the CLI is where the power is.

---

### Post by Gandalf_the_Grey on 2009-10-20
My F10 install is located at /dev/sda2.

The command "sudo mount /dev/sda2 /mnt -text3" replied with:

mount: wrong fs type, bad option, bad superblock on /dev/sda2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


In the syslog, it says:
[  324.085564] VFS: Can't find ext3 filesystem on dev sda2.

---

### Post by igknighted on 2009-10-20
Fedora defaults to using an LVM partition, so you probably need to install the LVM tools in ubuntu before it will recognize the partition.

---

### Post by Gandalf_the_Grey on 2009-10-21
Success.  Thanks for the help.

---

