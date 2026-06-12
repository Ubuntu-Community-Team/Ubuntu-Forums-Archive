---
title: "Windows Deployment Using Ubuntu Live"
date: 2010-09-23
forum: General Help
---

### Post by azurepancake on 2010-09-23
So, today I got a call from a client, requesting for me to setup Windows XP SP3 on 7 brand new laptops. 

How I plan to do this is to install Windows to one of the machines, then boot onto a Ubuntu Live disk, and backup all the Windows data into a tarball on to an external HD. 

Then on each machine, boot onto the live disk, format a NTFS partition using gparted, flag it as bootable and finally unload the tarball onto the partition. 

My question is, would this work and if so, would I need to use any kind of special parameters with the tar command? Maybe there are certain hidden files that tar won't backup without a certain flag?

I really do appreciate any advice or words of wisdom. 

Thank you very much!

---

### Post by egalvan on 2010-09-23
from this site for partimage...

[http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page)

quote:

> installing many identical computer images. For example, if you buy 50 PCs, with the same hardware, and want to install the same system on all of then, you will save a lot of time. Install on the first PC and create an image from it. For the 49 others, you can use the image file and Partition Image restore function. 


'dd' is another option

Isn't OpenSource wonderful? With all it's choices?

---

### Post by egalvan on 2010-09-23
Forgot to comment...

Since you are using XP, make **SURE** all hardware has valid drivers.
Manufacturers are starting to drop XP support.

You don't want to go to all the trouble of installing XP on all those machines, only to find that a piece of hardware is non-functional due to lack of driver.

---

### Post by azurepancake on 2010-09-23
Whoa, Partimage looks awesome! Thank you very much, this will make things much simpler.

The world of OpenSource is amazing. It feels so good not to be chained to one way of doing things that some massive, greedy company decided on. OpenSource has soul! ;)

Yeah, that's a very good point. I'm waiting for the client to get back to me with the model number so I can research the drivers.

Again, thanks for your help!

---

