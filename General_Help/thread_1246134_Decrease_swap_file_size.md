---
title: "Decrease swap file size?"
date: 2009-08-21
forum: General Help
---

### Post by pcgstudio on 2009-08-21
Hello,

I added a swap file size to my remote server with the terminal command, here:

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

unfortunately my / drive is now reading as 100% full of 4.7gb total size.

I added 1gb of swap file, as my system kept crashing, it stabilised however i think i added too much, and would like to take it down by 500mb, how can i resize it or delete it?

---

### Post by pcgstudio on 2009-08-21
okay thats been removed but it didnt solve the issue i had:

	
 	Used	 	Available
/	100.00%	
  	  	  	  	  	  	  	  	  	  
0B Free (4.7GB Total)
/var	14.27%	
  	  	  	  	  	  	  	  	  	  
4.1GB Free (4.7GB Total)
/home	8.62%	
  	  	  	  	  	  	  	  	  	  
197.0GB Free (215.6GB Total)
/boot	33.50%	
  	  	  	  	  	  	  	  	  	  
50MB Free (76MB Total)


basically my / is showing as full but i havent installed anything on it, i cleared the /tmp drive too :S

---

### Post by pcgstudio on 2009-08-21
i used this:

sudo dd if=/dev/zero of=/mnt/512Mb.swap bs=1M count=512

where is it located? can i delete teh swap file permanently?

---

### Post by P4man on 2009-08-21
oh dear, be very careful using that dd command !!!
You will wipe your entire hd with just a small typo or if you dont know exactly what you are doing. Besides,  there is no point in zero filling your swap file.

You're gonna need to boot a live cd and resize your partitions. Here is a nice forum post explaining it in detail:

[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)

---

### Post by P4man on 2009-08-21
oh and to reclaim the swap space,first swapoff:

```
sudo swapoff -a
```

Then edit /etc/fstab and remove the line pointing to the swap file. 
(shift-) Delete it from /mnt

---

### Post by dcstar on 2009-08-21
> **pcgstudio said:**
> i used this:

sudo dd if=/dev/zero of=**/mnt/512Mb.swap** bs=1M count=512

**where is it located**? can i delete the swap file permanently?

Yes.

---

