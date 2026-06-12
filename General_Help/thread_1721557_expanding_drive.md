---
title: "expanding drive"
date: 2011-04-04
forum: General Help
---

### Post by dazman19 on 2011-04-04
Hi

I have a VM with a 20gb virtual hard disk. I allocated another 80gb to it, and i can see it an use it. and mount it where i want it, But I actually want to expand the /dev/sda1 rather than mount the extra 80gb on a point. I can partition it back to free space. 

I have this command here: 
resize2fs /dev/sdXY

Where X is the device number and Y is the Linux partition. 

But I am a bit concerned that it may damage the original file system.

Is this what i want to be using?

---

