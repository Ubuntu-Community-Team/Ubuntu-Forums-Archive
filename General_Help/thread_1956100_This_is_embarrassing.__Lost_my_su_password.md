---
title: "This is embarrassing.  Lost my su password"
date: 2012-04-10
forum: General Help
---

### Post by rfsweitzer on 2012-04-10
This is embarrassing.I installed this version of Ubuntu this year.  I tried to do a su - to get to root so I can do an insmod of my driver.  It asked for my password. I entered my Ubuntu password I normally log in with and it said:
rfsweitzer@ubuntu:~/i2c_drv$ su -
Password: 
su: Authentication failure

Anyway I can get my su password without having to reload Ubuntu again?

Linux ubuntu 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by haqking on 2012-04-10
> **rfsweitzer said:**
> This is embarrassing.I installed this version of Ubuntu this year.  I tried to do a su - to get to root so I can do an insmod of my driver.  It asked for my password. I entered my Ubuntu password I normally log in with and it said:
rfsweitzer@ubuntu:~/i2c_drv$ su -
Password: 
su: Authentication failure

Anyway I can get my su password without having to reload Ubuntu again?

Linux ubuntu 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

no need to use root, use sudo and when asked for password, use the password you login with.

su means switch user or superuser, if you dont provide an account it defaults to root.

sudo means superuser do so do as a superuser or root for this action.

read [ROOTSUDO]("https://help.ubuntu.com/community/RootSudo") for more information

---

### Post by rfsweitzer on 2012-04-10
Thanks.  Problem solved.

---

### Post by haqking on 2012-04-10
> **rfsweitzer said:**
> Thanks.  Problem solved.

cool, remember to use thread tools to mark the thread as solved.

Cheers

---

