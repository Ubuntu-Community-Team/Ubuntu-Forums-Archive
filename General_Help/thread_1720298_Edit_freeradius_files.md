---
title: "Edit freeradius files"
date: 2011-04-03
forum: General Help
---

### Post by wanalex on 2011-04-03
Hello,

I've been following several turials and always end with the same mistake! I hope some of you guys will be able to help me :)

My config:

Ubuntu 10.04

I've installed a lamp server which works well.

Then I've installed freeradius with:

sudo apt-get install freeradius

It install itself properly and can be turned on and off with

sudo /etc/init.d/freeradius start

Then my problems start:

I need to edit /etc/freeradius/sql.conf but the folder containing freeradius has a white cross on it.
If i Chmod 777 -R /etc/freeradius/ the white cross disappear, and I can access and modify the files. 

But the freeradius doesnt want to start again once the folder has been chmod! --> [FAIL]

Every tutorials to set up freeradius for hotspot use the same commands but nobody seems to have this access problem!

What i am doing wrong please?

Thanks all for your help.

Alex

---

### Post by dcstar on 2011-04-03
> **wanalex said:**
> 
........
I need to edit /etc/freeradius/sql.conf but the folder containing freeradius has a white cross on it.
If i Chmod 777 -R /etc/freeradius/ the white cross disappear, and I can access and modify the files. 

But the freeradius doesnt want to start again once the folder has been chmod! --> [FAIL]

Every tutorials to set up freeradius for hotspot use the same commands but nobody seems to have this access problem!

What i am doing wrong please?

Thanks all for your help.

Alex

Never, **ever** change permissions on System folders and files - like /etc.

```
sudo gedit /etc/freeradius/sql.conf
```

---

### Post by wanalex on 2011-04-04
Thank you very much ! 

It worked perfect.

I still have difficulties with freeradius but I'll start a new thread for it.
Cheers 

ALex

---

