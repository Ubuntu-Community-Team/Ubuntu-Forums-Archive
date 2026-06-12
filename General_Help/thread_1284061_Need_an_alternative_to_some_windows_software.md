---
title: "Need an alternative to some windows software"
date: 2009-10-06
forum: General Help
---

### Post by aaronmarsh632 on 2009-10-06
Hi,

I use some software on windows called 'Easy Recovery Pro' by ontrack - for checking hard drives for bad sectors.

Does anybody know of an alternative for ubuntu which is just as good?

I have tried running through wine but it doesnt seem 2 work properly, and i have tried looking on alternativeto.net but im not having any luck.

Thanks

---

### Post by amauk on 2009-10-06
```
e2fsck -cy /dev/sda1
```
will perform a filesystem check of /dev/sda1, any bad blocks found will be added to the exclusion list to stop the block being allocated

---

### Post by anagor on 2009-10-06
I think you should look here:
[http://www.securityfocus.com/infocus/1902](http://www.securityfocus.com/infocus/1902)
and here (there is a PDF there with complete instructions)
[http://port25.technet.com/archive/2007/05/24/data-recovery-using-linux.aspx](http://port25.technet.com/archive/2007/05/24/data-recovery-using-linux.aspx)

It's not one aplication like you had with "Easy Recovery Pro", but a set of commands you can use to do the same job.

Hope it helps a little.

---

### Post by aaronmarsh632 on 2009-10-09
Thanks very much for the help pps, will use this l8r

---

### Post by alphaniner on 2009-10-09
If you are just looking to check for bad sectors, there's badblocks.

However, I test a lot of HDDs at work and I think the best tools are the drive manufacturer's bootable utilities: SeaTools for Seagate, Data Lifeguard Diagnostics for WD, etc.

---

