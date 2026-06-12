---
title: "Dual Boot with Gentoo"
date: 2009-10-19
forum: General Help
---

### Post by mikeym on 2009-10-19
Hi,

I'm wondering how to go about setting up my current ubuntu install to dual boot with gentoo. I've got a / partition and a /home partition (which I want to share with my gentoo install using a different username) and a new / partition to install gentoo onto. At the moment I have just the basic grub install you get with ubuntu. 

So how do I go about installing gentoo (I assume I just don't do any boot loader stuff and then setup grub in ubuntu to boot ubuntu or gentoo)?

---

### Post by ajgreeny on 2009-10-19
I have never tried Gentoo so can't comment specifically on that, but I quite often have two or three different linux distros on my machine with no problems at all.  One thing to be a little wary about is whether or not Gentoo will find Ubuntu and add it to the menu.lst or other grub configuration file that it may use; most distros are not nearly as good as Ubuntu at finding existing linux installs, so you may find yourself unable to boot Ubuntu without editing the grub config of Gentoo, not a major problem normally, I agree, but something to consider.  As you say, you could stop Gentoo from changing grub, and just edit the Ubuntu grub to add Gentoo, but that is your choice.

I think it would be best to have separate /home partition, but different user names as you suggest, but also to make a separate /data partition in which you can put all the docs, photos, videos, music etc etc, and thus save any possibility of doubling up all those files on disk.  Just make the data partition automount in the /etc/fstab of each distro, and away you should go.

Good luck.  Keep us informed of how you get on with Gentoo.

---

