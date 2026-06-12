---
title: "reccomended fixmbr or fdisk /mbr unsuccessful"
date: 2006-04-14
forum: General Help
---

### Post by can_climber on 2006-04-14
Hello,

  Like a fool I wrote grub to my mbr.  So only linux will boot, and when I select windowsME from the grub menu, grub just loads back up again.

  So I have a boot utilities floppy for windowsME.  Windows is on the the master drive and ubuntu on the slave.

  The computer boots from the disk to the A: drive.  I can switch to C: but I cant read the disk (ex. DIR does not work).  Is this standard?

anyway, I ran fdisk /mbr and the A: drive grinds for a bit and I get my prompt back.  I ran fixmbr and it complained that it could not read drive C:

From Linux I can read and write just fine to the windows drive.

Not sure what to do.  I am sure my menu.lst is fine.  And I have read how peoples mbr issues were fixed countless times by the trusty fdisk /mbr.  I am not sure why It wont work in this case.  any ideas?

I do find it ironic that I am posting what is essentially a windows problem on a linux forum:) 

-Caleb

---

### Post by PriceChild on 2006-04-14
I think that you should still be able to change your /boot/grub/menu.lst to allow windows to boot from grub.

What error is returned?

Maybe seeing your /boot/grub/menu.lst and an explanation of your partitions could help us figure out why me isn't loading, instead of letting you ditch linux and go back to windows ;)

---

### Post by nomail on 2006-04-18
try fixboot instead of fixmbr, worked for me...but still can't load Ubuntu...when I type grub-install in installCD rescue mode my C: Drive becomes unusable

Sorry for mistakes and bad english

---

