---
title: "The Best Way to Transfer Data to New Desktop Computer"
date: 2011-05-29
forum: General Help
---

### Post by OldBoy44 on 2011-05-29
Hi all,

I have a number of queries but will start with one. I presently operate 11.04 Classic (no effects). OS is NOT set up as dual boot. As I am considering purchasing a new Desktop, I am wondering what is the best way to recover such things as folders, Firefox bookmarks etc. for four users. 

I do have a external HDD which I guess could be used for a possible backup if that is the way to go! The new computer will probably have Windows 7 installed with which I assume I would probably dual boot.

I would appreciate any ideas on the best way to go!

Thank you.

---

### Post by katykat on 2011-05-29
The *best* way to go would be to install your present Linux drive on the new machine as a second hard drive (sdb) typically, but check system configuration for exact sequence with cd/dvds and card readers taking up drive slots....

If the architecture is not radically different Linux may function OK, but you would need to chroot from a Linux boot disk to double check. And then run grub-update to make a new bootsector for the Win drive. 

If it does not work, backup Linux to the external drive, making sure to keep your file permissions (such as TARring if the external is NTFS), and you may need to reformat the Linux drive and reinstall from the boot disk. At that point grub will find the Win drive and put grub on it, so it should dual boot just fine. 

There is also the option of networking the two machines together, but  have no clue for that, as I do not permit my Linux machine to take any connections from anywhere, including my own Win boxes. Linux has Samba on it to control the Win systems, however.

---

### Post by OldBoy44 on 2011-05-29
Thanks very much for your input katykat. Sorry I have not got back before now!
I will digest your answer with interest.

Cheers, :)

---

### Post by coldraven on 2011-05-29
Maybe you should first backup the entire /home folder to your external drive.
Then you could use Firefox sync (Tools>Set up Sync) for each user, that way they can get their bookmarks from any machine. 
Otherwise, katykat's idea sounds good.

---

