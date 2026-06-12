---
title: "Ghosting Drives with Ubuntu Live"
date: 2010-07-22
forum: General Help
---

### Post by Zythyr on 2010-07-22
On my desktop, my primary hard drive is running out of space and my secondard hard drive is bigger than my primary and plenty of space. I want to make my secondary hard drive my primary. 

I was planning to use Hiren's Boot CD to ghost my current primary to the second hard drive so that way I don't have to reinstall Windows and all the programs all over again. 

Is it possible to boot from Ubuntu live cd and ghost the hard drives instead of using Hiren's boot cd?

---

### Post by dFlyer on 2010-07-22
You might want to try Clonezilla.

---

### Post by lykwydchykyn on 2010-07-22
It's possible, using a command like dd or ddrescue, but you're probably better off using something like clonezilla or g4l.

---

### Post by Zythyr on 2010-07-22
So I am guessing I should just go with the hiren's boot cd since it has G4L. 

By the way, whats a better choice? G4L, Clonzilla, or Norton?

---

### Post by r+9 on 2010-07-22
This actually looks like fun, from the LiveCD, open a terminal.
This will likely clobber what you have on the bigger/2nd disk.  

first figure out what they are called
  sudo fdisk -l
/dev/sda1
/dev/sda2 
(for example)
then 

dd if=/dev/sda1 of=/dev/sda2

(you many need to add a 'sudo' to the dd command, I'm not sure)
Smarter people: correct me if I'm wrong, just off the top of my head.

---

### Post by lykwydchykyn on 2010-07-22
> **Zythyr said:**
> So I am guessing I should just go with the hiren's boot cd since it has G4L. 

By the way, whats a better choice? G4L, Clonzilla, or Norton?

It depends on what you want.  I prefer G4L, but it's just a question of which interface makes the most sense to how I think.


> **r+9 said:**
> This actually looks like fun, from the LiveCD, open a terminal.
This will likely clobber what you have on the bigger/2nd disk.  

first figure out what they are called
  sudo fdisk -l
/dev/sda1
/dev/sda2 
(for example)
then 

dd if=/dev/sda1 of=/dev/sda2

(you many need to add a 'sudo' to the dd command, I'm not sure)
Smarter people: correct me if I'm wrong, just off the top of my head.

That's the basic idea, and you definitely need root privileges.  It's not the best way to do it because you get no real progress meter, no handling of errors, etc.  But, assuming your disks are both functional and the second one is as big as the first, it should work fine.

---

### Post by billdougan on 2010-07-22
I can second Clonezilla, as I've used it in the past successfully.

If you're looking for something with a simple interface however, it doesn't get much more simple than Redo.

[http://redobackup.org](http://redobackup.org)

---

### Post by Zythyr on 2010-07-23
Well I think Hirens boot cd will be the best i guess? I just want to clone the primary hdd onto the secondary (slave) hard drive. Then I will physically swap them by opening up my desktop.

---

### Post by lykwydchykyn on 2010-07-23
I'm sure it will do the trick.

---

### Post by aeiah on 2010-07-23
once you've confirmed that the cloning worked, you'll still need to grow the partition using gparted or something. obviously, you should do this before formatting your old hdd, or before doing anything you wouldnt mind losing in case growing the partition(s) messes things up.

im not sure if the partition uuids will be cloned or not. if not, if you have fstab use uuid instead of partition number, you'll have to amend your fstab

---

### Post by Zythyr on 2010-07-23
> **aeiah said:**
> once you've confirmed that the cloning worked, you'll still need to grow the partition using gparted or something. obviously, you should do this before formatting your old hdd, or before doing anything you wouldnt mind losing in case growing the partition(s) messes things up.

im not sure if the partition uuids will be cloned or not. if not, if you have fstab use uuid instead of partition number, you'll have to amend your fstab

Wait now I am confused. My primary drive is 20GB and secondary is 40GB. If I clone primary to secondary hard drive, I will have to grow the partition? Why? I thought cloning just copies all the content from one drive to the other, why do I have to grow the partition?

---

### Post by schwabdale on 2010-07-23
> **Zythyr said:**
> Wait now I am confused. My primary drive is 20GB and secondary is 40GB. If I clone primary to secondary hard drive, I will have to grow the partition? Why? I thought cloning just copies all the content from one drive to the other, why do I have to grow the partition?

I think because you would be cloning the partition. When you move the partition to another drive, your 40 gig drive will have your 20 gig partition. If you want to use the entire 40 gigs, you will have to expand the partition. Unless you do some sort of disk to disk.

---

### Post by lykwydchykyn on 2010-07-23
> **Zythyr said:**
> Wait now I am confused. My primary drive is 20GB and secondary is 40GB. If I clone primary to secondary hard drive, I will have to grow the partition? Why? I thought cloning just copies all the content from one drive to the other, why do I have to grow the partition?

If you just cloned the contents of the partition, the drive wouldn't be bootable, because you wouldn't have copied the MBR and partition table.

---

