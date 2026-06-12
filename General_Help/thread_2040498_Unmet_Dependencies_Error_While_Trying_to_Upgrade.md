---
title: "Unmet Dependencies Error While Trying to Upgrade"
date: 2012-08-11
forum: General Help
---

### Post by miko5054 on 2012-08-11
this post is a duplication of this one [http://askubuntu.com/questions/173895/unmet-dependencies-error-while-trying-to-upgrade]("http://askubuntu.com/questions/173895/unmet-dependencies-error-while-trying-to-upgrade") i guess they cant help me there 

When I'm upgrading, get this error and can't install anything else
>  You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 krb5-multidev : Depends: libkrb5-3 (= 1.10+dfsg~beta1-2ubuntu0.2) but 1.10+dfsg~beta1-2ubuntu0.3 is installed
                 Depends: libk5crypto3 (= 1.10+dfsg~beta1-2ubuntu0.2) but 1.10+dfsg~beta1-2ubuntu0.3 is installed
                 Depends: libgssapi-krb5-2 (= 1.10+dfsg~beta1-2ubuntu0.2) but 1.10+dfsg~beta1-2ubuntu0.3 is installed
                 Depends: libgssrpc4 (= 1.10+dfsg~beta1-2ubuntu0.2) but 1.10+dfsg~beta1-2ubuntu0.3 is installed
                 Depends: libkadm5srv-mit8 (= 1.10+dfsg~beta1-2ubuntu0.2) but 1.10+dfsg~beta1-2ubuntu0.3 is installed
                 Depends: libkadm5clnt-mit8 (= 1.10+dfsg~beta1-2ubuntu0.2) but 1.10+dfsg~beta1-2ubuntu0.3 is installed
E: Unmet dependencies. Try using -f.


I tried to run > apt-get install -f but I still get the unmet dependencies error.

this is the apt-cache policy output : (i couldn't post it to much hyper links so i pastebin it)
[http://pastebin.com/zEACHge2]("http://pastebin.com/zEACHge2")

---

### Post by hal8000 on 2012-08-11
There are alternative ways to upgrade.
One way is to backup your data, music, files, etc and do a fresh install.
I always find this method quicker and more efficient and also have more
available space.

I would wait and see if anyone answers the dependency problem
You did not state which version you were upgrading, so I would assume its Ubuntu 11.10 to 12.04.

---

### Post by miko5054 on 2012-08-11
problem> **hal8000 said:**
> 
You did not state which version you were upgrading, so I would assume its Ubuntu 11.10 to 12.04.

that's correct

---

