---
title: "Opening UDF DVD ISO in Archive Manager"
date: 2009-11-05
forum: General Help
---

### Post by sanskaras on 2009-11-05
First of all I just wanted to edit a file in the iso and use it.

When I tried to open the iso archive manager basically told me to #(*# off in a nice way with a readme saying

"This disc contains a "UDF" file system and requires an operating system

that supports the ISO-13346 "UDF" file system specification."

So I installed udftools and libudf-0, didn't make any difference.  Archive manager didn't want to read it.

I tried several applications designed to mount the iso, none of them could mount it correctly for me to view the files.  Basically same thing the archive manager did.

I can make it mount successfully my manually typing
"sudo mount -t udf -o loop ..." but that doesn't help me edit the iso since the mount is readonly!

Anyone know how I can edit it?

---

### Post by conradin on 2009-11-14
Hey, Im having a similar issue. I have a bunch of ISOs on this hard drive.
(are you mounting the CD/DVD or an image?) for myself i'm not sure where to say mount. /dev/sd*  *== various partitions... 
anyways, theres a -w option in mount to get read write access. try that

---

### Post by sefs on 2011-05-06
How can this be solved and no solution posted.

---

