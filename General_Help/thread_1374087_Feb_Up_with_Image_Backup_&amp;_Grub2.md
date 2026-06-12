---
title: "Feb Up with Image Backup &amp; Grub2"
date: 2010-01-06
forum: General Help
---

### Post by Quarkrad on 2010-01-06
If I use Clonezilla to backup my Ubuntu partition I get all sorts of problems trying to re-install Grub2 after image reinstall.  If I backup the whole HD will this include Grub so when I re-install the image I get the whole thing back again?

---

### Post by Leppie on 2010-01-06
i've never used clonezilla, but i suppose that if it includes the drive's mbr in the backup, it should work.
mind you, if grub is set to use UUID's, this will miserably fail if the image is not restored onto the same original drive.

---

### Post by wkulecz on 2010-01-06
Grub2, UUID drive names and dynamic /dev naming cause me no end of grief.  I've yet to see an upside to any of it.  This is all even worse if you use raid.

First thing I do after installing is edit /etc/fstab and /boot/grub/menu.lst (haven't yet figured out where grub2 does it) to remove the UUID entries and replace them with /dev/sd or /dev/hd.  But then its alwyas a crap shoot if a new motherboard will have the IDE drives as /dev/hd or /dev/sd :(

Use the live CD to edit /etc/fsab and the grub boot setup file menu.lst aftr you figure out the grub2 menu.lst replacemnet.

Different is not better, better is better. I don't see any better in grub2 so far!

--wally.

---

### Post by sgbeamer on 2010-01-10
I am with wkulecz on this one.  This new grub has caused me 2 hours of pain trying to figure out how to change my boot order, when I was quite comfortable with the old way.  It's confusing as hell.  Run update-grub to get a list of what's on the menu then go to /etc/default/grub to change the order.  It was all in one place before.  Maybe there is some new great technical reason for the change but they sure made it tough for the desktop user like me.

---

### Post by motsteve on 2010-01-10
grub2 and uuid's violate a very fundamental rule: KISS

grub worked for years and years with hardly a complaint.

---

