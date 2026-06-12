---
title: "mounting a embedded ramdisk on a PC"
date: 2012-09-20
forum: General Help
---

### Post by MadBoat on 2012-09-20
howdy. 

So I have a ramdisk. I did not create it so I don't exactly know what it is, but it's called a ramdisk, and it's used during boot time of an embedded linux system im working with. Now if I want to edit the contents of that ramdisk? on one ubuntu system (11.10) I do a 'mount /ramdisk8M.image somedir/' and I get a nice directory that I can modify, and then reverse the process when I'm done. But the same command doesn't work on my 10.04 system; the mount command complains that it is not a block device.

now, if it was just me, I wouldn't care, I'd just use 11.10, but I am trying to document this process for poor newbies, who will be using a 10.04 distribution on our recommendation (for other reasons). So... what exactly is this thing I've been mounting, and how do I get the 10.04 mount to do what the 11.10 mount did for me? I presume there is some partition protocol that needs to be said explictly for the 10.04 mount but not the 11.10 mount?

---

