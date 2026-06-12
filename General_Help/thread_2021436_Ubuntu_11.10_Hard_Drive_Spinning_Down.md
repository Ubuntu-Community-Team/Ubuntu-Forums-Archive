---
title: "Ubuntu 11.10 Hard Drive Spinning Down"
date: 2012-07-09
forum: General Help
---

### Post by neutronforrest on 2012-07-09
Dear forum,

I have put together a nice little home server.  I have a ASrock mobo with the AMD e-350 cpu.  This mobo works great and I have 4GB of ram.  

I installed Ubuntu 11.10 (the desktop version) and I have a 250 gb hard driver where the os is installed.  I then have 2 500gb mirrored where I store all my important documents.  

My question is that I don't use the server very often.  I have checked the cpu temp and it stays constant around 53 degrees C.  Furthermore, the hard drives are quite warm.  I know they spin continuously.  Is there a way to spin down the drives when not in use? Does Ubuntu 11.10 have an idle mode?

I am very happy with this setup and just want to do something to preserve the hard drives from failure.  I have read that there is a way to spin down the drives.  Is this a good idea?  Some people have said that is better to leave them spinning all the time.

I welcome an ideas/suggestions
Chad

---

### Post by dino99 on 2012-07-09
i've had trouble using hddtemp, so i remove it via synaptic

---

### Post by neutronforrest on 2012-07-10
I have read online that there is a  /etc/hdparm.conf file that will allow me to spin down my hard drives.  However, I have a single HHD where the OS runs on.  I then have two 500gb mirrored HHD.  

Has anyone used this successfully with a raid 1 hard drive setup?  If so can you assist me in making the change to the config file.

Chad

---

### Post by jmore9 on 2012-07-10
I have always just let them spin away.  I personally believe that the stopping and starting of the drives puts more wear and tear on them.

Just my opionin , from all the drives i have had only have had 2 fail and they failed within 3 days of install.

I am thinking about getting another of the SSD drives but not sure about how they will last on regular usage compared to disks,  The one i have seems to work well but is only 6 months old so not a lot of life has been used up yet.

---

### Post by neutronforrest on 2012-07-10
See...my 250 gb hard drive is a few years old and the two 500gb are about a year old.  I don't mind leaving them spinning...just wondering what people experience with longevity of a server.

They run at 40C.  The cpu runs at 51c.

Chad

---

### Post by andrewkouri on 2012-07-19
i am trying to do this exact same thing on 12.04

I have set my drives to spin down, and they just spin right back up again!  I can't figure it out...

---

