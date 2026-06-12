---
title: "new person help"
date: 2010-08-22
forum: General Help
---

### Post by ceasaryahoo on 2010-08-22
I am using the firefox that came with the new version. this is all new to me. i can not seem to access the internet. my router does not see the connection, however i was able to get updates.
I do have several computers that is how i am writing this.
not too tech savy and first day with linux.

---

### Post by dougalkerr on 2010-08-22
Which version of Linux are you using and how old is the PC?

---

### Post by slooksterpsv on 2010-08-22
Can you browse to [http://74.125.45.105/](http://74.125.45.105/)

That should bring up google, does it?

If so, but google.com is not working, it's a resolver issue. So what we would need to do is log into your modem:
[http://192.168.0.1](http://192.168.0.1) or [http://192.168.1.1](http://192.168.1.1) or [http://192.168.2.1](http://192.168.2.1) or [http://192.168.254.254](http://192.168.254.254)

If one of those work we should see a name server, e.g. 205.171.52.36 - or some number like that, write it down.

Now click on Applications -> Accessories -> Terminal
Now type in: ```

gksudo gedit /etc/resolv.conf

```
Now change where it says: nameserver 192.168.x.x to the number we wrote down above, e.g. 205.171.52.36
Click on File -> Save and restart Firefox.

---

