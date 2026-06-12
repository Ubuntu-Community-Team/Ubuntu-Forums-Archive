---
title: "install rpm in fedora 14"
date: 2011-01-16
forum: General Help
---

### Post by catlover2 on 2011-01-16
Hello,
i just installed fedora 14 on an external HDD, and i am trying to install simple-ccsm-0.7.8-1.fc10.noarch.rpm
every time i try to install it it says:```
simple-ccsm-0.7.8-1.fc10.noarch requires python(abi) = 2.5
```
and does not installl.

thanks, Catlover

---

### Post by darkstaar on 2011-01-16
Hi,

I'm thinking that simple-ccsm-0.7.8-1 is a very old version.

Type in a terminal:
```
rpm -q --provides python | grep abi

```
I'd guess that you're running a newer version of python than 2.5 which is what this older version of simple-ccsm requires.

You would think that a version newer than 2.5 would satisfy the dependency but this isn't always the case. Anyway, that's surely why you're getting that error message.

---

### Post by catlover2 on 2011-01-17
What now?
```
[Reed@Reeds-M30X-Laptop ~]$ rpm -q --provides python | grep abi
python(abi) = 2.7
python-abi = 2.7
[Reed@Reeds-M30X-Laptop ~]$ 

```

---

### Post by darkstaar on 2011-01-17
> **catlover2 said:**
> What now?

Try the appropriate version of simple-ccsm for your distribution. Where did you find the RPM file simple-ccsm-0.7.8-1.fc10.noarch.rpm anyway? That's clearly written for Fedora 10 and won't install on your much newer F14 running Python 2.7.

You might want to check the repositories.

EDIT: Easier yet:
```
yum install simple-ccsm
```

---

### Post by bodhi.zazen on 2011-01-17
We are asking windows users to use windows forums , debian users the debian forums, and in your case I suggest you try the Fedora forums =)

that rpm is for fedora 10, either find a more up to date rpm or compile from source.

There was a bug report on this package

[https://bugzilla.redhat.com/show_bug.cgi?id=477948](https://bugzilla.redhat.com/show_bug.cgi?id=477948)

It was closed as "won't fix".

There is a repo here:

[http://repos.fedorapeople.org/repos/leigh123linux/compiz-fusion/](http://repos.fedorapeople.org/repos/leigh123linux/compiz-fusion/)

[http://repos.fedorapeople.org/repos/leigh123linux/compiz-fusion/fedora-14/](http://repos.fedorapeople.org/repos/leigh123linux/compiz-fusion/fedora-14/)

[http://repos.fedorapeople.org/repos/leigh123linux/compiz-fusion/fedora-14/i386/simple-ccsm-0.8.4-2.fc14.noarch.rpm](http://repos.fedorapeople.org/repos/leigh123linux/compiz-fusion/fedora-14/i386/simple-ccsm-0.8.4-2.fc14.noarch.rpm)

[http://repos.fedorapeople.org/repos/leigh123linux/compiz-fusion/fedora-14/x86_64/simple-ccsm-0.8.4-2.fc14.noarch.rpm](http://repos.fedorapeople.org/repos/leigh123linux/compiz-fusion/fedora-14/x86_64/simple-ccsm-0.8.4-2.fc14.noarch.rpm)

---

### Post by catlover2 on 2011-01-17
got it here:
[http://izhar.fedorapeople.org/simple-ccsm/](http://izhar.fedorapeople.org/simple-ccsm/)

nowhere to be found in the repos...

---

### Post by catlover2 on 2011-01-17
oops, didn't see your post, [[COLOR=#980101]**bodhi-zazen, **[/COLOR]]("http://ubuntuforums.org/member.php?u=89054")

worked great!

Thanks!
[[COLOR=#980101]****[/COLOR]]("http://ubuntuforums.org/member.php?u=89054")

---

### Post by Sef on 2011-01-17
Since this post is marked solved and has nothing to do with Ubuntu, it has been closed.

---

