---
title: "Gparted?"
date: 2010-11-18
forum: General Help
---

### Post by Tourdog on 2010-11-18
I finally gave XP the boot and now just have 10.04 on this box.    It's time to clean up, ie expand the Linux  "partitions".   Looking at my results posted how best to do that?

Should the .ISO cd that I made and used, boot to allow "unmounting" the required partitions?

TIA!

---

### Post by kwhatcher on 2010-11-18
Your best bet would be to boot from an install CD and let the installer handle the partitioning. You seem to have some crazy stuff going on with your partitions if all you have is ubuntu installed. 

***BE WARNED*** This will erase your entire hard drive.

Thanks,
Kerry Hatcher

---

### Post by pqwoerituytrueiwoq on 2010-11-18
partition layout is a mess
you only need one swap partition edit your fstab file on one of you partitions to use the other swap and delete the extra one
you can move your partition around but it takes forever and comes with a chance of data lose
here is mine
 anyone re ording partition on your hd will need to know what is on the partitions ex what ones are junk
i wold expand the extent partition to the right and delete a swap and move the other to the right wall
can the 1.5gb ext 4 partition be trashed so we can expand the other partition next to it?

---

### Post by Tourdog on 2010-11-18
Kerry,
sda1 was XP,  Gone and reformatted to ext4
       5 was Karmic Koala
       7 is     Lucid Lynx

I should have included this info in my intro.
Thanks,

---

### Post by pqwoerituytrueiwoq on 2010-11-18
i tryed having 2 ubuntu setups before but one just kept getting out of data (files) so i trashed the install
what do you want on the drive in the end

---

### Post by kwhatcher on 2010-11-18
So are you wanting to keep both of them?

---

### Post by Tourdog on 2010-11-18
kwhatcher & pqw......

Getting rid of 5  (Karmic) would open things up abit more.............   

This is what's been done so far...........

---

### Post by kwhatcher on 2010-11-18
Your image didn't work, could you try again please?

---

### Post by Sam Fallow on 2010-11-18
TBH I would back up all the important stuff and start again. All that deleting, moving, resizing, will take a long time and have the associated risk of loss of data. 

If you want to have a go, move all your data into the partition you would like t keep, e.g. move you 5.01 Gb from 7 to 5. Then (working from the live cd) I would start with unmounting the swap partitions, deleteing the smaller one and expanding the bigger one into that space. 

Then do the same for theother partitions. You can elect to instruct it to carry out many instructions and do them all, or go one at a time and see how it goes. 

here's a tidy sample for you. 
the ntfs partition is where I've been temporarily dual booting with with xp.
[IMG][IMG]http://i296.photobucket.com/albums/mm190/purplebear69/Screenshot--dev-sda-GParted.png[/IMG][/IMG]

---

