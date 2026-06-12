---
title: "System Restore Problem"
date: 2010-09-08
forum: General Help
---

### Post by Yarui on 2010-09-08
A friend has a netbook running a dual boot setup with Ubuntu (9.10, I think) and Windows XP.  She recently decided to run system restore on the Windows partition and can't boot into Windows anymore.  I told her I would help her fix it tonight, but before she gets here I figured it would probably be helpful to ask if this is a well known issue and if anyone has any suggestions on the best method of fixing it.

I planned on first making sure the grub is targeting the Windows partition correctly, but I suspect the problem could be that the system restore point she used was one from before she had a linux partition.  If that is the case does anyone know if this could potentially destroy the windows installation?

---

### Post by bodhi.zazen on 2010-09-08
You will have to look and see what you find, anything else would be speculation.

---

### Post by Rubi1200 on 2010-09-08
If she, or you, has an XP installation or recovery disc, I would suggest starting there with things like running chkdsk etc.

Also, if you are going to take a look at her setup, I suggest using an Ubuntu CD in live mode or something like Knoppix,

---

### Post by Yarui on 2010-09-08
She says her Ubuntu partition is working just fine, so I'm not sure a live CD is really necessary unless I end up having to do something to the Ubuntu partition that I can't really do while it is in use.

It is probably true that anything said here would just be speculation, but if someone has had a similar problem with system restore in the past it could be helpful to hear what they have to say on the matter.

---

### Post by Rubi1200 on 2010-09-09
Sorry, I should have clarified what I meant by using the LiveCD. I was thinking more along the lines of using it to explore the Windows filesystem to look for missing files etc.

---

### Post by garvinrick4 on 2010-09-09
If you boot into ubuntu and download this script to THE DESKTOP and then run this code below it will put a text file on your desktop that shows your whole boot info.
 Take that file and copy and paste it to this thread and you will have some users that will
look at that text file and know what is wrong and the fix. Here is the site to go to.
[SourceForge.net: Boot Info Script - Project Web Hosting - Open Source Software]("http://bootinfoscript.sourceforge.net/") 

```
 sudo bash ~/Desktop/boot_info_script*.sh 
```


If you can after you copy and paste to this thread highlight whole thing and 
hit the # sign in upper right corner and it will make it easier to read.

---

