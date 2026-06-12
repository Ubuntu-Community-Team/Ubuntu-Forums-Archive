---
title: "Grub error: no such device, invalid signiture"
date: 2012-07-26
forum: General Help
---

### Post by chrissound on 2012-07-26
Hello everyone. I have a ubuntu installation currently(it doesn't work sadly) and a windows 7 installation. 

I was on windows 7, and I got a BSOD, i get them every few days so no biggie. This time however every time I boot and get into grub and selec the windows 7 installation I get the following errors:

error: no such device: E6F8EBCDF8EB9A57
error: invalid signature

I've found this: [http://ubuntuforums.org/showpost.php?p=](http://ubuntuforums.org/showpost.php?p=) ... stcount=14

When I go to recovery mode, and 'drop in root'. I then run **cd /etc/default**, when I tried **cd grub** I get the message "*bash: cd: grub: not a directory*". 

If I run **ls** I do see grub present however?

Any ideas? I do have a linux mint lxde 12 disk or a ubuntu 10.10 disk here if need be. 

Thank you. =)

---

### Post by oldfred on 2012-07-26
Welcome to the forums.

Often invalid signature has to do with the NTFS partition boot sector.

Sometimes chkdsk or fixBoot from Windows repairCD will work.

May be best to post this link to BootInfo to see if other boot files are present. 

Boot Repair -Also handles LVM, GPT and separate /boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration.

---

