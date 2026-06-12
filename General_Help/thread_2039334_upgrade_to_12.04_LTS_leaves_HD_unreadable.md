---
title: "upgrade to 12.04 LTS leaves HD unreadable"
date: 2012-08-08
forum: General Help
---

### Post by rmead on 2012-08-08
upgrading 10.04 LTS to 12.04 LTS leaves HD unreadable.  Partition is unmountable (/dev/sda1 - the root partition).

The upgrade was a desktop upgrade using update-manager -d.  It reported success and attempted to reboot.

Hardware is Toshiba Satellite M55-S3293 laptop - 32 bit intel, generic laptop.

Should I expect the upgrade to proceed routinely?  If not, how do I get it to work?

---

### Post by Austin Texas on 2012-08-08
I had the same error message yesterday ( "Partition is unmountable" )
The problem was that I had an error in etc/fstab
Check the date on etc/fstab to see if a change was made. 
It would be great if you have a backup of your old fstab !
Post the fstab contents here.
It is not certain that is the problem, but it is one place to look.

---

