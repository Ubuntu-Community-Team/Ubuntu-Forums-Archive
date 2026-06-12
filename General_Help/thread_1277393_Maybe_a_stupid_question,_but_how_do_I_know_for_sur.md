---
title: "Maybe a stupid question, but how do I know for sure RAID is working?"
date: 2009-09-28
forum: General Help
---

### Post by Vunutus on 2009-09-28
I (hope) that I have software RAID set up the following way:

-500MB RAID1 mirroring array across 3 disks (plus one hot spare) mounted as /boot (since grub won't deal with RAID5)

-Everything else is a RAID 5 array across 3 disks (plus the hot spare)

Now, how do I actually KNOW that RAID is functional? What commands can I use to check on its status? So far my only evidence that it is working is that when I run a large file transfer (like sending 15GB clonezilla images to the server from a workstation), the "md2_raid5" process stays high on the output of top.

---

### Post by Vunutus on 2009-09-28
Bump

---

### Post by xxhopingtearsxx on 2009-09-28
[Please disregard this message.. it was a mistake]

---

### Post by JigglyWiggly_ on 2009-09-28
I am not going to be very useful, but onboard RAID in linux is a joke... I let Windows handle that, and it usually has better gui tools to inform you what is happening. And then run a VM of Ubuntu. 

Sorry I can't be of much help :( I tried doing a raid 5 with an ich10r intel sb once on Ubuntu, and it was awful... it saw all the hds seperately, and then I had to configure them inside the OS, which is a no-no to me.

---

### Post by Vunutus on 2009-09-28
In my experience, Linux software RAID is fantastic. It's about as fantastic as software RAID gets, and outperforms a lot of the crappy integrated hardware RAID controllers that come with low/mid range servers. 

Besides, I refuse to have Windows be a part of any server I administer :P

---

### Post by Vunutus on 2009-09-30
Bump.

---

