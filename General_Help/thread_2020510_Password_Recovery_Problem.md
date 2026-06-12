---
title: "Password Recovery Problem"
date: 2012-07-08
forum: General Help
---

### Post by loybanks on 2012-07-08
Need password recovery for ubuntu 11.10. I just finished trying recover method from [http://www.psychocats.net/ubuntu/resetpassword/](http://www.psychocats.net/ubuntu/resetpassword/), but it didn't work. 

That method went thru recovery mode to root according to instructions at that url. Message I got back was...authentication token manipulation error. The method was slick but unproductive. 

So still need a way to recover password. This Linux machine had been working, updating, etc just fine. I have no idea what happened with the password. Totally bamboozled here!

---

### Post by steeldriver on 2012-07-08
sounds like you might have missed a step? without it the /etc/passwd file can't be updated:

>  In recent versions of Ubuntu, the filesystem is mounted as read-only, so  you need to enter the follow command to get it to remount as  read-write, which will allow you to make changes: 
```
mount -o rw,remount /
```

---

