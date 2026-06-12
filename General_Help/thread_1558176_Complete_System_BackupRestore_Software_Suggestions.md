---
title: "Complete System Backup/Restore Software Suggestions"
date: 2010-08-21
forum: General Help
---

### Post by CFet on 2010-08-21
Hi All,
So I got my system to be nice and stable =) so I'd like to back it up. 

I'm after some software that would let me copy absolutely everything and restore it should I monkey up my setup in the future. I want to be able to insert a disc, usb or other media then click "restore" then reboot and have my system right back where it was down to every last detail. I'm hoping to do a test restore tonight to familiarize myself with the process.
Cheers,
Chris

---

### Post by TimEnid on 2010-08-21
remastersys - go to system>administration

---

### Post by CFet on 2010-08-22
> **TimEnid said:**
> remastersys - go to system>administration

I'm not sure what you're referring to here, are you making a suggestion? Is remastersys a program? I don't see it listed in the menu specified. 

Anyone else have suggestions? G4L confused the crap out of me. I'm still new to Linux hence my sense of urgency to back up my rare occasion of a stable setup before I muck it up again :P

---

### Post by earthpigg on 2010-08-22
he is talking about [remastersys]("http://www.geekconnection.org/remastersys/"), an outstanding tool that is (unfortunately) not available in the repositories but available at the website i linked.

---

### Post by Vrroom on 2010-08-22
remastersys is really good....you can not only make backups but also can make a bootable image of your entire system with all applications and data in your home folder. So if something goes wrong you can reinstall your system from the image as it is with no change in files and configuration.

---

### Post by john newbuntu on 2010-08-22
Another utility is clonezilla [http://sourceforge.net/projects/clonezilla/](http://sourceforge.net/projects/clonezilla/) It has the option of backing up your entire hard disk(including any Windows installs), backup partitions, copy/restore partitions/disks etc. Slightly non-intuitive interface, but has worked for me several times.

---

### Post by majortom67 on 2010-08-22
I do quote remastersys. Get the right repository with Google (sorry, I don't have it with me). Install it.
You can either:
- use the shell:
1) sudo remastersys dist cdfs
2)  (when finished above): sudo remastersys dist iso
3) burn the ISO
4) sudo remastersys clean (delete all temp files)

OR

- use the simple GUI:
1) distcdfs optio
2) distiso option
3) clean option

Please note: the Home folder will not be backuped, it makes no sense as you may have it backuped frequently with other sw (Sbackup, Grsync, ecc ecc). You may then re-install your whole system from the ISO CD or DVD and restore the Home folder apart. Logout/login to have your preferences loaded.

Also note: on my MacBookPro 2010 this method gives me a problem: looks that the xorg.config files is not copied back. I therefore need to remove and reinstall nVidia video drivers; I believe that other folders (etc, var, usr/local) should be backuped apart as SBackup includes them bu default. Is just a thought. Hope somebody can confirm this in order to have also graphics automatically working.
Desktop image is also gone lost... but the rest is fine and fast to do.

---

