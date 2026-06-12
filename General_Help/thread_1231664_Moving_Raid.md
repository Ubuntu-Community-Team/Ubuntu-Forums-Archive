---
title: "Moving Raid"
date: 2009-08-04
forum: General Help
---

### Post by jpsage on 2009-08-04
I have a new motherboard, processor and  raid under 8.04. This is my mythtv master. It has been upgraded several times and is getting a little strange and I want to start anew with 9.04. I am going to save my mythtv shows to the raid (as mpeg files) and will create a new build. 
Before I start the transition, I will want to make sure that I don't screw up the raid. It is a raid5 with four sata drives on a m3n78-vm motherboard.

Thanks for any advice. 

john.

---

### Post by jpsage on 2009-08-07
Just in case someone else needs to do this I am answering my own post.

Well that was easy. Build the new system, install mdadm, reboot the computer and mount the raid. 

I did a test run by installing 9.04 and learned that mdadm scans for and finds an existing raid as if it was a single disk. 

john.

---

