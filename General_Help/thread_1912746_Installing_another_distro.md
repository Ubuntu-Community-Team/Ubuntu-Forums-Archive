---
title: "Installing another distro"
date: 2012-01-21
forum: General Help
---

### Post by oldgreygary on 2012-01-21
Hello,

Firstly, I am no 'technical wizzo' so please be patient. I currently have Ubuntu 11.10 running and Windows XP. This is on a dual boot setup, uses Grub(?) to choose between options

Anyway, what I would like to do is install another distro without upsetting the already installed Ububtu and Windows XP.

Can anyone advise me on the best course of action? Thanks.

Gary

---

### Post by KdotJ on 2012-01-21
Hey, I'm not exactly a wizard on setting up and configuring grub.. so I'll leave that to someone more knowledgeable. However, do you want to install the distro to give it a spin? Because a great way would be to use a virtual machine (I recommend VirtualBox), then you can try as many distros as you want without upsetting your current setup.

---

### Post by sudodus on 2012-01-21
0. Test the new operating system live from a CD or USB drive. Don't try to install, if it doesn't work live! (But some systems cannot be tested live.)

1. ***Backup your data before tampering with your hard drive!***

2. Select or make a partition

If you have a spare partition, install the new distro into that, otherwise shrink one partition and use the free space for a partition for the new distro. Run a live session with gparted to edit the partition table. This is risky, so you need a backup.

3. Install to the partition that you have selected! If it is a good distro, it will update grub so that all present operating systems will be bootable. Otherwise this can be done afterwards with live session by a Ubuntu installation CD or USB drive.

comment: All linux versions installed can use the same swap partition, so you need not make a new one.

---

### Post by raja.genupula on 2012-01-21
Install what ever the other distro you wanna install on other partition.After installing it boot into your ubuntu and open the terminal and do this

```
sudo dpkg-reconfigure grub-pc
```
and in the installation choose your ubuntu's hdd partition. That will gives your grub back to Ubuntu .

from that point if you wanna make any changes to Ubuntu grub , install Grub customizer . you can get that from my link.

All the best.

---

