---
title: "Any solution to low memory issues for Eeepc 900 and NBR"
date: 2010-09-01
forum: General Help
---

### Post by stuartcox on 2010-09-01
I have Eeepc 900 and  NBR latest addition. 4gbSDD and 16gbHD. I have only minimal software and some necessary ones such as Rythmbox etc. 

After normal updates I find my 4gb SDD is running extremely low with expected results. Hanging etc. 

I have tried to find a solution to this but cannot at the moment. I remember being able to move over some process or files to the 16gb drive but do not have the know how or cannot find the comment to do this.

Any help is much appreciated. If i cannot im going to have to ditch the pc. Dont want to as it is perfectly good and ubuntu is getting great. 

Thank you

Stuart

---

### Post by boudewjn on 2010-09-01
hi,

had this recently, using netbook 10.04:
backed up
removed some excess programs
added gparted and mc
set up 4 GB /home and /usr partitions on the 16 GB drive
copied /home and /usr there (the new partitions show are mountable via the normal graphic menu) 
had an ubuntu install stick ready in case of messing up (in that case to be used in demonstration mode)
delete /home and /usr on 4 GB drive
without logging off adjust /etc/fstab (see man fstab and man mount)
when my fstab was not right straight away I could still enter recovery mode and fix it
lastly I fine tuned sizes of the partitions and added a second swap file (resulting in one each on 4 GB and on 16 GB).

fstab was a bit complicated by the Ubuntu's UUID stuff (you will see), normal device names should have worked I think, but I just looked up the partition UUID's with gparted (CTRL-C there) and pasted them in fstab with sudo gedit (CTRL-V there).

If that is too complicated, use the 16 GB drive for a new install, and move your 4 GB /home stuff there.

success Boudewijn

---

### Post by boudewjn on 2010-09-01
oops, reading this:

deleting /home and /usr on the 4 GB drive is not exactly right.
just directories/files below them.

these stay in the tree on the 4 GB drive.
and the new partitions are to be mounted on these.

regards Boudewijn

---

### Post by stuartcox on 2010-09-01
Thank you for your prompt reply. A great help.

I will let you know the results later today and comment on any complications or ease of action for future use.

Stuart

---

### Post by stuartcox on 2010-09-07
Hi. 

I am sorry but i will need a bit of a newbie walk through regarding this. 

Thank you in advance..

Stuart

---

### Post by dcstar on 2010-09-07
Do a web search for a separate /home partition, there are already detailed instructions out there.

---

### Post by stuartcox on 2010-09-07
Ok. No problems. I will work it out and post a step by step for future use. Thanks for your previous help. 

Stuart

---

