---
title: "Problem with DvDs...."
date: 2006-06-04
forum: General Help
---

### Post by PriceChild on 2006-06-04
Im' currently trying to install BF2 with cedega... however when i put the DvD in the drive, /media/cdrom-1 is only made read and executable by root and group.... not "other" You can see everything as root btw.

Not having this problem with cds, and this is the first time its happenned in linux :(

Please help, Pricey.

UPDATE

Seems to be just a problem with that DVD, just loaded "The Mighty Boosh" Into the drive and all worked fine.

The thing is that i've installed BF2 before when i had Breezy.... What's going on?

---

### Post by PriceChild on 2006-06-04
bump

---

### Post by eqisow on 2006-06-04
OK, well clearly you don't want to install BF2 as root. What you could do, however, is rip the DVD to an ISO, then mount the iso and install from there.

```
sudo  dd if=/dev/cdrom of=BF2.iso
sudo umount /media/cdrom0
sudo chmod 777 BF2.iso
sudo mount -o loop BF2.iso /media/cdrom0
```

Now run the installer from /media/cdrom0.

When you are done, run the following:

```
sudo umount /media/cdrom0
```

You can now delete the iso if you wish.

If this were a Linux native game, there would be no problem doing this. However, since you are running it Cedega the BF2 installer may cause a fuss due to copy protection stuff. Then again, Cedega should treat it as a CD since it's in the CD directory, so perhaps it will be ok.

If what I've told you doesn't work, you could always download the game from BitTorrent, and install that way. Should get rid of both the DVD and the copy protection problem.

Edit: This should probably be in the 'Ubuntu Gaming' section, but I understand that you dind't realize it was only a BF2 problem at the time. :)

---

### Post by PriceChild on 2006-06-04
Ok thanks for the help, I'm going to try it, but i know it won't work because of the copy protection issue.

This really isn't a gaming forum point... there's nothing wrong with the game. It is ubuntu being mean and only mounting it for root :(

Is there a way i could possbily mount for myself? or mount with different permissions from the command line?

Pricey

Ok... this is wierd, i went into disks-admin, disabled access to the drive, re-enabled it and for some reason it now works!

I'm not complaining, still wierd though! Pricey

---

### Post by eqisow on 2006-06-04
I've done it with a few other games in Wine when installing from the disk wasn't working for some reason. I've never had trouble, but who knows.

The only reason I thought it was a gaming issue was because it was only BF2. I assumed it had something to do with the game disk itself.

At any rate, I'm glad you got it sorted out. Have fun playing.

Cheers :)

---

