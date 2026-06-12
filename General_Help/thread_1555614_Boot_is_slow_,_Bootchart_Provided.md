---
title: "Boot is slow , Bootchart Provided"
date: 2010-08-18
forum: General Help
---

### Post by jman6495 on 2010-08-18
Hey , My boot is slow , what would you recommend ?
ps.it was like this before i upgraded to 10.10

uploading bootchart now

[IMG]http://www.lhlinux.org/members/uploads/jordan-laptop-maverick-20100818-1.png[/IMG]

for proper quality :)

---

### Post by oaxacamatt1 on 2010-08-18
After only a quick look at your Bootchart.  I noticed a few things I would knock off right away.  There are at least two things I do when I get my hands on Ubuntu.  
1) Download BUM - bootup manager from Synaptic and turn off the services you don't use BEING careful not to turn off the 'wrong' ones.  I turn off bluetooth, speech-dispatcher, rsync for example.
2) goto System/Preferences/Start up Applications and turn off apps there too, like bluetooth, evolution alarm, gnome login sound, etc.  ALSO being careful not to turn off useful 'stuff'.

Other than that your computer may be slow and old. I don't know...  If you discuss hardware related issues it might be a good idea to include some discussion about your HW.  

As an aside, I dislike Bootchart for the reason it does not really give a beginner much useful info.  I kinda sez, yes this takes a while and this doesn't, so what...  Sometimes there is nothing one can do.
Cheers,
Matt

---

### Post by stijnblommerde on 2010-10-11
slow boot. 47 secs.

previous version (10.04 lts) was much faster. cannot find the cause. anyone?

bootchart:
[http://img29.imageshack.us/img29/3719/laptopmaverick201010112.png](http://img29.imageshack.us/img29/3719/laptopmaverick201010112.png)

---

### Post by markmill73 on 2010-10-11
> **oaxacamatt1 said:**
> After only a quick look at your Bootchart.  I noticed a few things I would knock off right away.  There are at least two things I do when I get my hands on Ubuntu.  
1) Download BUM - bootup manager from Synaptic and turn off the services you don't use BEING careful not to turn off the 'wrong' ones.  I turn off bluetooth, speech-dispatcher, rsync for example.
2) goto System/Preferences/Start up Applications and turn off apps there too, like bluetooth, evolution alarm, gnome login sound, etc.  ALSO being careful not to turn off useful 'stuff'.


Thanks those points helped me out, even if i have an old machine. :P

---

### Post by SlugSlug on 2010-10-11
> **markmill73 said:**
> Thanks those points helped me out, even if i have an old machine. :P


I seem to remember uninstalling udev a on a older dist.. may help ?? or may break it :)

---

