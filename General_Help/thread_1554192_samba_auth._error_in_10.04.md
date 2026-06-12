---
title: "samba auth. error in 10.04"
date: 2010-08-16
forum: General Help
---

### Post by ARhere on 2010-08-16
Hi Everyone,

I have a NAS that I installed 10.04 on and installed the GUI Samba through "Ubuntu Software Center".  The NAS machine main account is "andrew" and that is the owner of all the data in the shares (*a lot of files*) but I want a separate user name and password to be able to access the data shares.  I set up "Samba Users" so the local account "andrew" uses user name "family" and a different password.
[IMG]http://www.arhere.com/samba.png[/IMG]

I then have local machines (*all Ubuntu, different versions.*) mount the shares using the following fstab entries.
```
//192.168.1.10/Music	/home/jill/Music	cifs auto,username=family,password=********,uid=1000,umask=000,user   0 0
//192.168.1.10/public	/home/jill/Public	cifs auto,username=family,password=********,uid=1000,umask=000,user   0 0
//192.168.1.10/jrfiles	/home/jill/Documents	cifs auto,username=family,password=********,uid=1000,umask=000,user   0 0
```

What happens is this works fine for a day, and then without any changes, attempts to mount after 24 hours result in...
```
mount: block device //192.168.1.10/***** is write protected, mounting read-only
mount: cannot mount block device //192.168.1.1/***** read-only
```

When the NAS used 8.04 LTS, this worked without any issues, but now after about a day, this stops working.  Rebooting the NAS and this will work again, only to stop after a day.

I found [this Bug report]("https://bugs.launchpad.net/ubuntu/+source/samba/+bug/563805") but it does not seem to be the same issue.  HELP! 

-AR

---

### Post by ARhere on 2010-08-18
Bump!?

-ar

---

### Post by ARhere on 2010-08-19
Help Please?

I am shocked to think that this is not affecting anyone else, as it is a common application.

Can someone else at least verify this please?

-AR

---

