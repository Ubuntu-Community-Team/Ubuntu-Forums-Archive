---
title: "Where are downloaded packages stored?"
date: 2010-03-09
forum: General Help
---

### Post by h3llb0y~ on 2010-03-09
Hi, im using ubuntu karmic for a while now.....but i had to change my computer. I don't want to lose all packages i had installed since i have to pay for my downloads, and downloading big packages costs a lot :(
Can anyone tell me where the packeges are stored in the filesystem?

---

### Post by sisco311 on 2010-03-09
/var/cache/apt/archives/

---

### Post by L0neRanger on 2010-03-09
I don't think the packages you install will be stored indefinitely. Also when you're talking about a new install, it's always better to update/upgrade with a internet connection - dependencies.

Another Option: Image your drive and then use that image to process your new computer.

---

### Post by h3llb0y~ on 2010-03-09
image a 30Gig drive is not possible for me :(

---

### Post by rahilm on 2010-03-09
> **h3llb0y~ said:**
> image a 30Gig drive is not possible for me :(
How big is the drive without /home and /media and /boot and /tmp and /dev and /proc
and what is the size of /var/cache/apt/archives ?

---

### Post by h3llb0y~ on 2010-03-10
var/cache/apt/archives was small....~130MB
i did a ubuntu reinstall as well.....
For anyone who reads this thread in the future, i used aptondc to do the job.

Cheers

---

### Post by myphone on 2010-03-10
probably downloaded packages stored in your my documents folder.

---

### Post by rahilm on 2010-03-11
> **h3llb0y~ said:**
> var/cache/apt/archives was small....~130MB
i did a ubuntu reinstall as well.....
For anyone who reads this thread in the future, i used aptondc to do the job.

Cheers

its good it worked with you. with me it failed miserably. I spent an entire day dragging packages one by one because there was a certain package that would crash the program when added. Then i realised that it made an iso which is good only if burnt to a physical disk...so i used other force methods to re-install my softwares.

---

