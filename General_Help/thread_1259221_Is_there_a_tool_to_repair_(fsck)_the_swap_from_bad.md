---
title: "Is there a tool to repair (fsck) the swap from bad blocks?"
date: 2009-09-06
forum: General Help
---

### Post by frenchn00b on 2009-09-06
Is there a tool to repair (fsck) the swap from bad blocks? 
  
apparently it is not possible to fix a harddisk from bad blocks. Is that possible?

---

### Post by P4man on 2009-09-06
To remap bad blocks, you need to do a "lowlevel format" with a  program from the harddisk manufacturer. This is destructive for your data!

You can download the ultimate bootcd, it has tools for all common harddisk vendors:
[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

That said, if it really has bad blocks, Id seriously consider replacing the drive..

---

### Post by frenchn00b on 2009-09-06
> **P4man said:**
> To remap bad blocks, you need to do a "lowlevel format" with a  program from the harddisk manufacturer. This is destructive for your data!

You can download the ultimate bootcd, it has tools for all common harddisk vendors:
[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

That said, if it really has bad blocks, Id seriously consider replacing the drive..

there is solutions sure under linux. 
the harddisk has those clusters, the same, since 10years ;) never changed

---

### Post by P4man on 2009-09-06
No, you can't. Modern harddrives make abstraction of the actual sectors and remap bad sectors to spare sectors themrselves. This is invisible to the bios and therefore the OS. You need a program from the hd manufacturer to get around that and talk to the HDD firmware. Things have changed in the last 10 years :)

BTW, as far as i know modern (ie, less than 10yr old) drives do this automatically all the time. The only reason you'd still see bad sectors, is if the drive ran out of spare sectors, which almost certainly means its dying and you should replace it.

---

### Post by zmdmw52 on 2009-09-06
> **frenchn00b said:**
> Is there a tool to repair (fsck) the swap from bad blocks? 
  
apparently it is not possible to fix a harddisk from bad blocks. Is that possible?
[FONT="Arial"]
Have a read at this article - [http://www.pcplus.co.uk/node/3108](http://www.pcplus.co.uk/node/3108)


You will need a Linux Live CD, I personally prefer PartedMagic ([www.partedmagic.com](www.partedmagic.com)), as that includes all the needed tools (programs).[/FONT]

---

### Post by frenchn00b on 2009-09-06
> **P4man said:**
> No, you can't. Modern harddrives make abstraction of the actual sectors and remap bad sectors to spare sectors themrselves. This is invisible to the bios and therefore the OS. You need a program from the hd manufacturer to get around that and talk to the HDD firmware. Things have changed in the last 10 years :)

BTW, as far as i know modern (ie, less than 10yr old) drives do this automatically all the time. The only reason you'd still see bad sectors, is if the drive ran out of spare sectors, which almost certainly means its dying and you should replace it.

5min ago, woody just rechecked my swap from bad blocks ;)
I made a shot of it. So it shall be possible

---

