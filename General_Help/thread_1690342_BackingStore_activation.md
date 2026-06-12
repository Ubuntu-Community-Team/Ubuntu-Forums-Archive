---
title: "BackingStore activation"
date: 2011-02-18
forum: General Help
---

### Post by Valentin630 on 2011-02-18
How to activate the ``BackingStore''  when you start your X11 server?
The origin of the question is :
 [http://wwwasd.web.cern.ch/wwwasd/cgi...stpawfaqs.pl/6]("http://wwwasd.web.cern.ch/wwwasd/cgi-bin/listpawfaqs.pl/6")
 		                   		  		  		  		  		 		 			 				 				* 					 						P.S. please don't close the thread, Yes, I asked this question in other forum, but nobody can answer it over there*

---

### Post by dabl on 2011-02-18
My google-foo isn't helping much either, but I found this:

[http://ubuntuforums.org/showthread.php?t=686459](http://ubuntuforums.org/showthread.php?t=686459)

The link to compiz-fusion.org is broken.  However, the second post suggests that if you made a /etc/X11/xorg.conf file, and all it had in it was:

```
Section "Device"
     Option "BackingStore" "True"
EndSection
```

that might work.  The risk being, I have read that the latest xserver-xorg does not even read the /etc/X11/xorg.conf file unless a proprietary driver is being used.

Good luck.

---

### Post by Valentin630 on 2011-02-18
Thank you, I know this, but it is a semi-solution because it works only on one desk-top,
if you change to other one and back you loose the content of the window

---

