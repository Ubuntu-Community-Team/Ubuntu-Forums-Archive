---
title: "Uninstall Karmic"
date: 2009-11-16
forum: General Help
---

### Post by labtek on 2009-11-16
Hello to the group and good day.

I was using Ubuntu 9.04 on my IBM Thinkpad A31 quite happily in a dual boot situation with Windows XP Home.

In a moment of weakness, I upgraded Ubuntu to 9.10 with less than satisfactory results. Most notably, 9.10 locks up frequently, among other problems.

I'd like to uninstall 9.10 and put 9.04 back in the previous dual boot with Windows XP.  At present, the 30 Gb hard drive is partitioned with 15 Gb allocated to Windows and 15 Gb to Ubuntu.

Can I re-partition the hard drive in some manner to keep Windows and safely uninstall 9.10 and re-install 9.04?

Thanks in advance for any thoughts.

---

### Post by Kevbert on 2009-11-16
Just install via CD with manual partitioning. select the old Ubuntu partition with mount point / and formatted ext3 (you may need to delete the old Ubuntu partition first and then reselect it). The swap partition can be left as is and will be detected automatically on install.

---

### Post by P4man on 2009-11-16
Do you have a wubi install ? Or did you install karmic to its own partition?

---

### Post by bestlasik on 2009-11-16
> **labtek said:**
> Hello to the group and good day.

I was using Ubuntu 9.04 on my IBM Thinkpad A31 quite happily in a dual boot situation with Windows XP Home.

In a moment of weakness, I upgraded Ubuntu to 9.10 with less than satisfactory results. Most notably, 9.10 locks up frequently, among other problems.

I'd like to uninstall 9.10 and put 9.04 back in the previous dual boot with Windows XP.  At present, the 30 Gb hard drive is partitioned with 15 Gb allocated to Windows and 15 Gb to Ubuntu.

Can I re-partition the hard drive in some manner to keep Windows and safely uninstall 9.10 and re-install 9.04?

Thanks in advance for any thoughts.
Good idea !
your information same to me:p

---

### Post by t0p on 2009-11-16
Do you have a 9.04 cd?  If not, you'd better grab the .iso from somewhere and burn it to disk.

Okay, now boot from the live cd and select to install.  Choose manual partitioning, and tell the partition editor (Gparted I think) to reformat the Ubuntu 9.10 partition as ext3 (or ext4 if you like) then install 9.04 to that partition.  Click OK or Apply or whatever.  And install.

Job done!  But remember, *don't* tell the installer to install to the whole disk, don't tell the partition editor to reformat your Windows partition.  Oh, and **back up any files you don't want to lose!!!**  Better safe than sorry eh?

---

### Post by P4man on 2009-11-16
> **t0p said:**
> D
Okay, now boot from the live cd and select to install.  Choose manual partitioning, and tell the partition editor (Gparted I think) to reformat the Ubuntu 9.10 partition as ext3 (or ext4 if you like) then install 9.04 to that partition.  

Thats assuming the OPs didnt do a wubi install. Im not sure how to uninstall wubi, but I thought it was as simple as removing it through windows add/remove programs.

---

### Post by labtek on 2009-11-16
Thanks to all who posted responses.

Using my 9.04 installation CD, I re-partioned the 9.10 portion of the hard disk as ext3 and then re-installed 9.04 there.

On re-booting, I now have 9.04 running as before in a dual boot situation with Windows XP.

I'm grateful for the advice.

Thank you again.

---

### Post by ximhot on 2009-12-04
Just don't try 9.10 on IBM A31 or T30. The display doesn't work.

---

