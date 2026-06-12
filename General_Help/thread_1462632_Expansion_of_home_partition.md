---
title: "Expansion of /home partition"
date: 2010-04-25
forum: General Help
---

### Post by space_boy on 2010-04-25
I am reaching the upper limit of my /home partition. As shown in the image attached, my /home is located in /sba3, and I have an additional partition for storage in /sba6. Since Lucid Lynx is about to be released, is it possible using the GPart software on the LiveCD to remove the /sba6 partition, add 1 GiB to my swap partition and the rest to /home without messing up all of my data in /home? So far in my search of the forum I have not come across anything exactly touching this subject, so I am requesting some guidance before proceeding. I have already back up all of my data for a full clean install if it comes to that.

---

### Post by mikewhatever on 2010-04-25
The info you are looking for is not Ubuntu specific, but rather some general partitioning stuff, usually present in, for example, Gparted documentation. 
Anyway, the answer is 'Yes you can'. Delete the extended partition and add the unallocated space to where required.

---

### Post by space_boy on 2010-04-25
Thank you, that is just the response I needed.

---

