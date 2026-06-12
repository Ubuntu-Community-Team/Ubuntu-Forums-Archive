---
title: "MSI 845E MAX fakeraid w/ no raid bios"
date: 2010-03-28
forum: General Help
---

### Post by bwarbis on 2010-03-28
Greetings,
    I have an MSI 845E Max Motherboard. I just purchased the computer USED. I have no manual and from all accounts of the online manual, this MB is doing the impossible....

   Connected to this MB are 2 WD 60GB hard drives. Bother are recognized in the bios. When booting from the live CD, and running the disk utility I can plainly see that there are the 2 drives and one striped array (using both of those drives).

    There is no settings in BIOS for any array. If I remove 1 of the drives, the disk utility sees only 1 drive but still sees an array. I can find no way to eliminate, recreate, oe manipulate this array in any way.

To make matters worse, I attempted to install an older FREEBSD, using it it saw both drives (no raid). Using their Disk utility I re-partitioned both drives and continued the install. Unfortunately the version I had was an older one and it could not complete the FTP install (And I would rather have Ubuntu anyways). Though through this action I believe that I have destroyed the integetery of the raid and if it is to be used it needs to be fixed......

So.. how do I fix something that my BIOS is not supposed to be capable of doing? Has anyone else experienced this issue.

BTW, Attempting to install XP, IT could see NO Drives.

---

### Post by mosibfu on 2010-04-11
its a fakeraid (driver raid) any motherboard can do that.. only some motherboards support booting from such an array.

i just replaced my mobo's and went from an array with 2x 500 gb disks (bootable), still they are recognized as an array on my current mobo (not bootable tho), i suppose something in the master boot record of the disks is flagged and telling ubuntu is an array.. since your windows does not have the raid drivers installed, it will not work under windows (windows will not see the array)

i am at the moment investigating how to revert the raid thingy.

hope that explained what is going on :)

-mosibfu

---

