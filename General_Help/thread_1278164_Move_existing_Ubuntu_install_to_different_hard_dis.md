---
title: "Move existing Ubuntu install to different hard disk"
date: 2009-09-29
forum: General Help
---

### Post by WhiskeyAlpha on 2009-09-29
Hi guys,  first post so take it easy ;)

I've had a headless fileserver running Ubuntu (Xubuntu to be precise) for a couple of years now (currently 8.04.3 LTS).

I started out with a 80GB Western Digital drive and later added a 1TB Samsung spinpoint to cater for my growing audio/video collection.  I followed a guide to move my /home directory to the 1TB, whilst leaving the 80GB as my root (and boot) drive.

However, the 80GB drive is on its last legs and is making some awful sounds.  What I would really like to do is move everything onto the larger drive and get rid of the old 80GB drive altogether.

I'm not sure what the best method would be though.  I don't mind creating a new partition on the larger drive (by shrinking the existing one) to mount /.  There just seems to be a ton of questions involved that I'm not confident enough to tackle alone yet.  E.g. how do I go about reconfiguring GRUB? How do I ensure my permissions and ownerships remain intact? What command would be better dd or cp (and with which flags)?

Hopefully you guys can point me in the right direction :)

Thanks in advance,

WhiskeyAlpha

---

### Post by Giblet5 on 2009-09-29
If it were me, I'd grab a new 80GB drive for $15 and rebuild the OS install with a newer version. It's the second shortest path.

The shortest is to replace the 80G with an identical 80G and use 'dd' to image the one to the other.

---

### Post by the_squircle on 2009-09-29
> **WhiskeyAlpha said:**
> 
Hopefully you guys can point me in the right direction :)


Indeed we can :D

If it were me, I'd download and boot a copy of [PartedMagic](http://partedmagic.com/), which I've used many times to move and repartition things. After that, use [this guide](http://linuxmint.com/wiki/index.php/How_to_repair_your_grub) to repair GRUB, which is a really easy guide to follow. (I know it's for Mint, but Mint is practically Ubuntu; it'll work).

Cheers!

---

