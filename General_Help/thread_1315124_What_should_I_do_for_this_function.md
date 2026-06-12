---
title: "What should I do for this function"
date: 2009-11-05
forum: General Help
---

### Post by jason.tan on 2009-11-05
I have two computers in my dormitory now.One is laptop and another is desk-top.
 The deskp-top is put there to be coverd by dust,which is such a waste of resouce anyway.
 Therefore,I have an idea that I am ready to set the desk-top as linux server to let the classmates without linux system ssh my computer to pracise using linux system.(Very long sentence!haha,beg your pardon)
 Now , I have downloaded the open-ssh server package and it can be “sshed”.
 However,I have no time to set the account for them one by one so I am thinking of build a php page to let them register by themselves.
 PHP can excute shell commond but here a problem comes:some commonds must be excute by the root.
If a company wanna do the similar job,it will work under root or use "expect"?
Or any other more powerful method?


Any one tell me?
thx


[http://www.godmaker.cn/?p=34](http://www.godmaker.cn/?p=34)

---

### Post by soapBAR2 on 2009-11-05
I'm assuming you don't care about users having root access and all the damage they can cause (either by accident or maliciously) to you or your network. Why not run the PHP daemon/script as root, and have it auto-add all new users to /etc/sudoers? Or make a group "sudoers", add sudoers to /etc/sudoers and then add all new users to the "sudoers" group?

---

### Post by jason.tan on 2009-11-05
In fact,I actually don't care the security.(Noting important in my desktop)

However,I wanna set it as a safe server because I will need to do this function in company in the future.What should I do?

---

### Post by grandtoubab on 2009-11-05
[http://www.ubuntu.com/products/whatisubuntu](http://www.ubuntu.com/products/whatisubuntu)

[http://www.ubuntu.com/products/whatisubuntu/serveredition](http://www.ubuntu.com/products/whatisubuntu/serveredition)

---

### Post by jason.tan on 2009-11-05
what if i don't use ubuntu server edition?

---

### Post by grandtoubab on 2009-11-05
Nothing, I thaught you want use it :lolflag:

Maybe you need only information on networking

See [http://ubuntuguide.org/wiki/Ubuntu:Karmic](http://ubuntuguide.org/wiki/Ubuntu:Karmic)
section 5 [http://ubuntuguide.org/wiki/Ubuntu:Karmic#Networking](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Networking)

---

### Post by jason.tan on 2009-11-06
What about LDAP?
Although I duno what is,someone recommended it to me.

---

