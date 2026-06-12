---
title: "Reinstalling xp"
date: 2010-03-29
forum: General Help
---

### Post by yus4eel on 2010-03-29
Ok so ive haad ubuntu 9.10 for about 2 months but want to go back to xp
so i got my disc, inserted it, restarted my computer and chose to boot from the installation disc.
the screen says 
disc loading...... 

but after about a minute loads into ubuntu

so i tried installing the disc through wine and when i choose the option that says "install windows"
 it loads for 10 seconds then says

“Windows Setup has encountered a problem and needs to close. We are sorry for the inconvenience.

You will need to rerun setup in order to install Windows. Choosing dynamic update during setup will possibly remedy this error.”

how can i do a clean install of xp without haveing to dual boot or anything, and i dont mind erasing/formatting my hard drive

---

### Post by Calash on 2010-03-29
Are you sure your XP disk is good?  That sounds a bit like a bad disk, or one that was waiting for you to press a key.


Try booting to the disk again and when it says "Disk Loading" tap a key, just to see if that is what it is looking for.

If that does not work you can load up the Ubuntu LiveCD and delete all your partitions from gparted, then try again.

Remember that you will lose all of the information on your hard drive.  Be sure to backup before.

---

### Post by Mark Phelps on 2010-03-29
As you discovered, you can't use Wine to install MS Windows, only to install applications.

The problem could be that the disk is already full with existing Linux partitions -- which XP will not be able to understand.

So, the suggestions of booting from an Ubuntu LiveCd and using it to erase all the partitions on the disk should remedy that problem.

---

### Post by llawwehttam on 2010-03-29
This is a common problem. XP cannot see ext partitions. Boot the ubuntu live cd and use the partition editor to wipe the HDD and format it to NTFS. Then boot from the xp cd and hit enter when it tells you to and it should install just fine.

---

