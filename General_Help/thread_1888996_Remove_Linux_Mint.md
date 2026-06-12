---
title: "Remove Linux Mint"
date: 2011-11-30
forum: General Help
---

### Post by UncleMonty on 2011-11-30
I am dual booting linux mint and ubuntu on a laptop. Is there anyway I can remove the linux mint partition and merge the partition with ubuntu?

---

### Post by mikewhatever on 2011-11-30
Sure, use Gparted from an Ubuntu live CD/USB.

---

### Post by sirvinniei on 2011-11-30
> **UncleMonty said:**
> I am dual booting linux mint and ubuntu on a laptop. Is there anyway I can remove the linux mint partition and merge the partition with ubuntu?
with merging do you mean puttin g the stuff you have on mint to ubuntu?
if so, You have to start up ubuntu mount the linux mint partition and move the things you want from mint to ubuntu and then delete the mint partition with gparted

---

### Post by Rex Bouwense on 2011-11-30
Yes.  Using Gparted, you delete the partition on which Mint is installed.  The space then becomes unallocated.  You then resize your Ubuntu partition to include the unallocated space.  See:

[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

for a tutorial.

Beat out by two because of my two finger typing speed and inability to find the tutorial quick enough.  Good job.

---

### Post by jjex22 on 2011-11-30
Hi there! yes, it's quite easy - first make sure Ubuntu's bootloader is in charge by running 

sudo update-grub

then back up - always backup before you change a hard drive - make sure abolutely nothing you want is on your mint partition.

Do the deed with gparted -  I recommend getting gparted as a live cd - so non of the partitions are mounted when you do it.. get it[ here]("http://gparted.sourceforge.net/download.php")

Either way in gparted you just right click the linux mint partition, left click delete, then click apply.

When this action finishes you just right click the ubuntu partition and click resize - use the slider to move the partition to fill up the space (so that preceeding and following both say 0) and click apply. - partitioning done.

boot into Ubuntu and again sudo update-grub to remove the mint entry

Couple of things to remember - If linux mint is before ubuntu on the drive, you may have to use the live cd to fix grub, as the partition number in grub may have changed (but you could try booting using the old mint entry - it occurs to me mint and ubuntu are so similar this may work)

Also if linux mint is before ubuntu resizing will take ages - expanding to the right just adds free space, expanding to the left means moving every sector, as partitions fill up from the beginning.

if linux mint is after ubuntu - very easy - it should all work after partitioning.

---

