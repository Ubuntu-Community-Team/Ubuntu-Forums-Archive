---
title: "Vista in Virtualbox"
date: 2011-09-28
forum: General Help
---

### Post by meddyuk on 2011-09-28
Hiya, I wondered if you could help me?

I currently run Natty dual booted on my Dell Machine with Vista. I tend to use Vista for Itunes and anything that won't run on Ubuntu. However, i'm a sucker for Ubuntu and use that as my main OS.

I originally partioned my 160GB hard drive so that 80GB was NTFS (vista) and 11Gb was ext2 for Ubuntu, the rest was root etc for Ubuntu.

I want to maximise the use of my Ubuntu system and thought that by installing Virtualbox this may help.

My question is twofold. 1. Is it worth me just simply formatting the 80GB NTFS partition and turning it into ext2 and telling VB to use the 20GB from there

2. What will happen to my MBR?

Cheers.

Meddy.

---

### Post by howefield on 2011-09-28
You could reformat your windows partition but depending on where you have installed Grub, you may wipe that out. It isn't particularly difficult to reinstate, but you'd need to do it.

Fwiw, I get better results running windows vms from ntfs file systems than if they were installed into an ext partition.

---

### Post by coffeecat on 2011-09-28
I've done something similar to what you are wanting to do. My sda1 is a dedicated partition for virtual machine files for VirtualBox. VB puts all its VM files in a ~/VirtualBox VMs folder, so what I did is to mount sda1 to /mnt/VirtualDiscs in /etc/fstab, chown the sda1 filesystem to myself, and then replace "~/Virtual Box VMs" with a symlink of the same name linking to /mnt/VirtualDiscs. I formatted sda1 as ext4 and when first using VB got a warning message saying that a kernel bug could potentially cause filesystem corruption when VMs were in an ext4 fs and that I needed to tick one of the options in the VM settings. I can't remember which one, off-hand.

Regarding Vista, I can't enable Aero when it's running in a VirtualBox VM, even though I can get compiz, wobbly windows and transparency in Ubuntu Lucid running in a VM with the same Natty host.

---

