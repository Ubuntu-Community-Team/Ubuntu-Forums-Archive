---
title: "problems with rdiff-backup to external USB media"
date: 2009-10-21
forum: General Help
---

### Post by yanvolking on 2009-10-21
Hello Community,

I can use rdiff-backup to backup files and directories within my home directory structure.  Example:

  	 	 	 	 	 	  yan@yan-laptop:~$ rdiff-backup /home/yan/elektra /home/yan/backup 
 yan@yan-laptop:~$  
 
But when I try to backup the same archive to an external USB memory stick, I get the following problem:

  	 	 	 	 	 	  yan@yan-laptop:~$ rdiff-backup /home/yan/elektra /media/16GB_USB/USB_backup 
 Warning: hard linking not supported by filesystem at /media/16GB_USB/USB_backup/rdiff-backup-data 
 
after this when I look at the content of the USB stick, I can see that the rdiff-backup-data file has been created (as is also the case in the backup to /home/yan/backup) but the contents of the elektra directory has not been copied to the USB stick.

I would like to use rdiff-backup to backup large volume multimedia archives from one external HDD to another.  I am afraid that if I cannot backup small archives from my home directory to a mere USB stick, there is not much chance of doing this with large archives on external HDDs.

Could this have something to do with the format system of the supports (ext3 for the home directory environment; and FAT32 for the USB stick)?

Thanks for your replies

---

### Post by dcstar on 2009-10-22
> **yanvolking said:**
> 
.......
Could this have something to do with the format system of the supports (ext3 for the home directory environment; and FAT32 for the USB stick)?


Yes, FAT is a primitive filesystem that does not support Linux attributes.

---

### Post by yanvolking on 2009-10-22
Hi David,

Thanks for your reply.  Just one interesting point.  rdiff_backup works backing up to external hard disk drives formated in NTFS (I tried it with success yesterday).  Does this mean then that NTFS is more "friendly" towards linux than FAT?

Can USB memory sticks then be formated in NTFS?

thanks

---

### Post by yanvolking on 2009-10-22
Hello Community,

I've just found out that with FAT32 formated USB sticks, although the message :

"Warning: hard linking not supported by filesystem at /media/16GB_USB/USB_backup/rdiff-backup-dat"

appears, the cursor justifies left and flashes oin and off.  ie: it does not go back to the user prompt.  This is because the backup is taking place.  Knowing this I waited the required amount of time for the backup to complete, and then the cursor gave the user prompt.  After that I checked the destination USB stick and it had the complete backup on it.  So apparently, it would seem we dont have to worry about the warning message, unless you want to do a bit of "HARD LINKING" whatever that may be.



CONCLUSION : rdiff-backup is really a wonderful tool.

Still, If anyone wants to explain what HARD LINKING is, the info is very welcome.

:)

---

### Post by QLee on 2009-10-22
[QUOTE=yanvolking]
Still, If anyone wants to explain what HARD LINKING is, the info is very welcome.[/QUOTE]

Instead of trying to cover everything in a post and reinventing the wheel, here is a link to a description, if you have specific questions after reading it come back and someone will try to answer.
[http://en.wikipedia.org/wiki/Hard_link](http://en.wikipedia.org/wiki/Hard_link)

---

