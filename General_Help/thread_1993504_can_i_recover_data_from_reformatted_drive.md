---
title: "can i recover data from reformatted drive?"
date: 2012-06-02
forum: General Help
---

### Post by sdpagent on 2012-06-02
Ok im an idiot and got my two, 2TB drives mixed up and reformatted the wrong one to fat32 from ntfs.

Is it possible that i could recover the data in any way? At the moment Im running the gparted data recovery thing but its taking forever and Im not even sure if thats the right route to go down. I think its for if you deleted a partition, not for if you reformatted the whole drive.

Regards,
Stu

---

### Post by scottbomb on 2012-06-02
I recently did the same thing. I don't know about a Linux solution but there is a Windows freeware called recuva that did a deep scan on my 2 TB drive (that had been quick-formatted and re-partitioned) and it recovered hundreds of my files.

---

### Post by jim_deadlock on 2012-06-02
Have a look at testdisk in the Software Centre, it contains photorec for recovering all types of files.

---

### Post by sdpagent on 2012-06-02
Thanks scott, im running the recuva thing now. said it would take 22 hours a few hours ago so left it running. We shall see

---

### Post by Paqman on 2012-06-02
You should be able to recover most of it, as long as you didn't write too much new data to the disk. Photorec is the bomb, it'll find anything that's still there.

---

### Post by sdpagent on 2012-06-03
I switched to photorec today when i discovered that the recuva program was stuck at 100% for over an hour, and had eaten up ALL my ram on the machine, at 8 gigs. 

Im not holding my breath for the photorec program as all im getting is 'Error reading sector xxxxxx' (where x changes) havent seen anthing that suggests anything was recovered.

Also it seems to think it will do it in just over an hour, whereas recuv program took a whole day! maybe the command line/linux is just better I dont know. 

Stu

---

### Post by sdpagent on 2012-06-03
> **sdpagent said:**
> I switched to photorec today when i discovered  that the recuva program was stuck at 100% for over an hour, and had  eaten up ALL my ram on the machine, at 8 gigs. 
 
 Im not holding my breath for the photorec program as all im getting is  'Error reading sector xxxxxx' (where x changes) havent seen anthing that  suggests anything was recovered.
 
 Also it seems to think it will do it in just over an hour, whereas recuv  program took a whole day! maybe the command line/linux is just better I  dont know. 
 
 Stu
 
 I have since re-enabled brute force, checks for a few more file types,  and im not getting failed to read commands, and its now going to take 15  hours. Fingers crossed.

Lots of recovered files already! Unfortunately all the names are gone. Thats going to make it fun fun fun. 
 
 Stu

---

