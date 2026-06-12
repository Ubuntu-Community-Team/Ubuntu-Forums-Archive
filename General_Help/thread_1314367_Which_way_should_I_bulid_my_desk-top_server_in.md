---
title: "Which way should I bulid my desk-top server in?"
date: 2009-11-04
forum: General Help
---

### Post by jason.tan on 2009-11-04
I have two computers in my dormitory now.One is laptop and another is desk-top.
 The deskp-top is put there to be coverd by dust,which is such a waste of resouce anyway.
 Therefore,I have an idea that I am ready to set the desk-top as linux server to let the classmates without linux system ssh my computer to pracise using linux system.(Very long sentence!haha,beg your pardon)
 Now , I have downloaded the open-ssh server package and it can be “sshed”.
 However,I have no time to set the account for them one by one so I am thinking of build a php page to let them register by themselves.
 PHP can excute shell commond but here a problem comes:some commonds must be excute by the root.


If a company wanna implement a similar function,which method is safer?


Or any other powerful idea?I am a green hand thx!


[http://www.godmaker.cn/?p=34](http://www.godmaker.cn/?p=34)

---

### Post by Giblet5 on 2009-11-04
You can do it with php and sudo.

Just add www-data to the admin group, then edit sudoers and list the useradd, etc, commands as requiring no password for user www-data.

You do know that your users will break your install, right?

Probably within five minutes...

---

### Post by cariboo on 2009-11-04
It might be a wonderful idea in your mind, but you are setting yourself up to be cracked, it takes less than 2 minutes to set up an account for someone.

I would also suggest you allow key based logins only, with a pass-phrase. If you allow people to setup their own accounts, you will more than likely be rebuilding your server weekly. 

One of our members set up a server and allowed ssh access to it by everyone, the server was useless in less than an hour.

---

