---
title: "samba wont start on boot"
date: 2010-07-04
forum: General Help
---

### Post by ulao on 2010-07-04
I have installed samba and it will not start on boot, but if I :

```

nmbd stop
smbd stop
smbd start
nmbd start

``` 

It comes up. I read that there were a few bugs about this but Didnt think 10 would still have issues. Maybe it does?

---

### Post by ulao on 2010-07-04
getting confused here. is there a init.d and something called a service or is that the same thing. Because every service manager i install shows the same thing as rcconf. According to them smbd is running and runs at start up. Yet when I boot up samba is not working.  I can simply run smbd start and all is well.
nplane this to me.

---

### Post by ulao on 2010-07-04
And now for something completely different.
```

rm  /etc/init.d/smbd
smbd start

```
Ok not sure how that works but it does, now I test my file share ( all works fine )
```

smbd stop

```
Hmm, still working?

now reboot, and test ( I can not get to the file share )
```

smbd start

```, Still not sure how this is running if the file is removed?
I test the file share. Oh looky there it work. what in the heck am I missing here? Surly there is at least one kind linux users that can e

---

### Post by ulao on 2010-07-05
> This bug was fixed in the package samba - 2:3.4.0-3ubuntu5.3 - This version is lower then what I have, is there a way to upgrade samba ( maybe I have an old version ) I have  2:3.4.7~dfsg-1ubuntu3. I think 3.5.4 is the latest, how do you install that?

I I ripped out samba completely and reinstalled it

smbstatus
> 
Samba version 3.4.7
PID     Username      Group         Machine
-------------------------------------------------------------------

Service      pid     machine       Connected at
-------------------------------------------------------

No locked filesis it not possible to install the final version of 3 ? My sources are up to date and so is sptitude.


So its available in 10.10
[https://launchpad.net/ubuntu/+source/samba](https://launchpad.net/ubuntu/+source/samba)

---

