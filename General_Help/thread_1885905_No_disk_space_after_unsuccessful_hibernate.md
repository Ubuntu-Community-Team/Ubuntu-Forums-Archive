---
title: "No disk space after unsuccessful hibernate"
date: 2011-11-24
forum: General Help
---

### Post by fyzmat on 2011-11-24
Hello,

I use ubuntu 10.04 and yesterday I tried the hibernate function for the first time. It did not work and I returned after a clear desktop after restart. Unfortunately my system hard drive is almost full (there was about 1.5GB space before hibernating). I guess that the system tried to save the image for hibernation to my system drive and run out of space.

How can I troubleshoot it? I would really like to get those 1.5GB back.

Thanks,
Tomas

---

### Post by jerrrys on 2011-11-25
**Remove all the packages** 	from /var/cache/apt/archives and /var/cache/apt/archives/partial 	folders:  	  
[LIST]
[*]sudo apt-get clean
[/LIST]
 
[LIST]
[*]**Remove 	all expired packages** from /var/cache/apt/archives and 	/var/cache/apt/archives/partial that are no longer available for 	download:  	
[/LIST]
 
[LIST]
[*]sudo apt-get autoclean
[/LIST]
 "*Not available for download*" does not mean the user should save them - normally these files have been replaced or are no longer needed.  
 
[LIST]
[*]**Remove unneeded dependencies** 	which are no longer needed:  	
[/LIST]
 
[LIST]
[*]sudo apt-get autoremove
[/LIST]

---

