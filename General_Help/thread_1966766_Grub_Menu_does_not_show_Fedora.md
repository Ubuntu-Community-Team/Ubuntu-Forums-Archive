---
title: "Grub Menu does not show Fedora"
date: 2012-04-27
forum: General Help
---

### Post by fantab on 2012-04-27
This never happened before. I always dual boot Ubuntu and Fedora and use Grub from Ubuntu. I have just installed Ubuntu 12.04 amd_64. 
Grub menu does not detect list Fedora installation. Fedora grub is installed to its own / partition. 

11.10 (My previous install of Ubuntu) did not have any such problem. Grub actually detects other linux os even when grub from those distros is not installed. On my friend's desktop too there is same issue, however here other OS like windows and linux mint are detected but not fedora. 

Please help...

---

### Post by oldfred on 2012-04-27
Did you run this:

sudo update-grub

If that does not show your Fedora install then run the bootinfoscript from this  and post the link it provides, so we can review your exact configuration:

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or Create BootInfo report & post the link to a run of boot info script so we can see your exact

---

### Post by fantab on 2012-04-27
I figured it out. Unlike before I had to mount the Fedora Partition before running *sudo update-grub*. This too is strange because never before I had to mount the respective partition to update Grub.

Wonder what changed between 11.10 and 12.04 to affect this?

Thanks oldfred.

---

### Post by oldfred on 2012-04-27
That is new to me also. Is partition some unique format?

I do not have all my other Ubuntu installs mounted and it found those at least thru beta.

But, I have turned off os_prober and just add my own boot stanzas to 40_custom as otherwise it is too confusing.

---

### Post by fantab on 2012-04-27
> **oldfred said:**
> That is new to me also. Is partition some unique format?

No. The partition is formatted as Ext4 with / as mountpoint. And yes other Ubuntu partitions are detected the usual way.

---

### Post by jringoot on 2012-06-01
I have a multiboot system, installed in this order: 
1. windows7 
2. ubuntu 12.04 
3. fedora 17

I recently got an update of ubuntu -> fedora got lost in the grub menu.

Reason was: ubuntu was installed on regular logical drives but fedora created an LVM on install.
Solution: (Booted in Ubuntu)
-sudo apt-get install lvm2
-activate the volumegroup where fedora was installed (lvmtools or simply with palimpsest a gui disk-manager, is gnome-disk-utility as a package see [http://en.wikipedia.org/wiki/Palimpsest_Disk_Utility](http://en.wikipedia.org/wiki/Palimpsest_Disk_Utility))
-mount the volumes needed (/boot and /) (can be done easily with palimpsest as well)
-sudo grub-update

Now I have fedora choice back in grub.

To get back the fedora grub, I read this document from fedora:
[http://fedoraproject.org/wiki/GRUB_2](http://fedoraproject.org/wiki/GRUB_2)

And did this when booted in fedora:

Your Machine may vary:

grub2-install /dev/sda

---

### Post by jringoot on 2012-06-01
> **fantab said:**
> I figured it out. Unlike before I had to mount the Fedora Partition before running *sudo update-grub*. This too is strange because never before I had to mount the respective partition to update Grub.

Wonder what changed between 11.10 and 12.04 to affect this?

Thanks oldfred.

Thanks fantab: Your hint to mount the partition, made me find that the lvm-partitions of fedora were not mountable because they are lvm and lvm was not installed in ubuntu.

---

### Post by dmbtimmyb212000 on 2012-08-30
> **jringoot said:**
> Thanks fantab: Your hint to mount the partition, made me find that the lvm-partitions of fedora were not mountable because they are lvm and lvm was not installed in ubuntu.

Thanks to all for the input:  I multi-boot SolusOS, Ubuntu Precise, Zorin, Mint 12, and Fedora 17.  

**apt-get install lvm2 did the trick (actually performed this in Debian). ** 

opensource freedom #FTW

---

### Post by YannBuntu on 2012-08-31
Hello

> **fantab said:**
> Unlike before I had to mount the Fedora Partition before running *sudo update-grub*.

You can mark yourself as affected by [https://bugs.launchpad.net/ubuntu/+source/os-prober/+bug/1038093](https://bugs.launchpad.net/ubuntu/+source/os-prober/+bug/1038093)

---

### Post by HughR on 2012-08-31
I have this problem.  I don't think that my Fedora 17 installations are using LVM.  Certainly all I have to do the make Ubuntu 12.04's update-grub2 or grub-mkconfig find Fedora partitions is to mount them, which I do with a simple click of each in the file manager.  I don't have to install LVM on my Ubuntu.

BTW: it really is easier to keep track of partitions if you label them.  Those labels show up in the file manager, for example.  I don't know why labelling isn't made more convenient.  Being old school, I just use e2label(8).

---

