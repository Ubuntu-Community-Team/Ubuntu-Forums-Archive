---
title: "Prevent updates of certain packages?"
date: 2006-04-17
forum: General Help
---

### Post by tschew on 2006-04-17
Hi,

I'm running clearlooks-cairo on my dapper install but unfortunately apt wants to "update" these packages with the official clearlooks debs. Is it possible to prevent this like with gentoo's package.mask?

Thanks.

---

### Post by 5-HT on 2006-04-17
Hi, yup it can be done by 'holding' packages at their current version.

Easiest way would be to just set them to be held via synaptic. 

Can be done through command line as well.

This thread discusses the matter and walks you through how to hold packages:[ http://ubuntuforums.org/showthread.php?t=161190]("http://ubuntuforums.org/showthread.php?t=161190")

*EDIT: After reading your post again, looks like I may have misread it and you don't want Ubuntu's clearlooks debs to replace your own.
Holding may not work in this instance if the package names are different.
In that case the 'force version' option in synaptic (should have a command line equivalent as well) may help if holding the package does not. 


Hope this helps.

---

### Post by tschew on 2006-04-17
Thanks, holding the version works great in synaptic... unfortunately it has no effect on apt itself, but that is OK.

---

### Post by 5-HT on 2006-04-17
[quote=tschew]Thanks, holding the version works great in synaptic... unfortunately it has no effect on apt itself, but that is OK.[/quote] Glad it worked.
I use aptitude myself, and there is a really easy way to hold them from the command line ```
 aptitude hold <package> 
``` 
I was looking for a similar way to do it with apt-get, but couldn't find any reference in the man page (maybe it is just as simple as a 'apt-get hold <package>'?).

Looks like you can do it on the command line at the dpkg level though, which should hold for apt-get.

---

