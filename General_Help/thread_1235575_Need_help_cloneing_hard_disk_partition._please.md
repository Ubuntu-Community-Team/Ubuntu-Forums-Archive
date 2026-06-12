---
title: "Need help cloneing hard disk partition. please"
date: 2009-08-09
forum: General Help
---

### Post by morepowerr on 2009-08-09
I will try to make this short as not to bore the reader. 
 
  I just installed 9.04 netbook remix on my new acer aspire 1. Every thing is dual-booting nicely. But what I need to do now is make a clone or img/iso of the acer restore partition. Just encase something go's terribly wrong. Will looking for a answer I came across this link.

[http://boards.fool.com/Message.asp?mid=21436613&sort=whole](http://boards.fool.com/Message.asp?mid=21436613&sort=whole)

 But mainly I just need to know how to save the hole acer restore partition into 1 bootable .img or .iso . So that if anything happen I have the means to restore the netbooks hard disk.

 Thanks.

---

### Post by Barafu Albino Cheetah on 2009-08-09
You can simply use _dd_ command, but be very carefull with it! to copy, for example, /dev/hda4 to file, use [FONT=Courier New]dd -if=/dev/hda4 -of=/home/disk.iso.[/FONT]  You will get a byte-to-byte image.  To restore , exchange the operands.   Again, be VERY carefull with dd,  (**d**angeous **d**iskkiller)

---

### Post by slakkie on 2009-08-09
[www.clonezilla.org](www.clonezilla.org)

---

### Post by morepowerr on 2009-08-09
I will look in to clonezilla thanks slakkie. Don't won't to play with dd unless I have no other route. I hope it make a bootable iso/img. Will see after I look in to it more. 

 And thank you both for you help :-D

 powerr

---

