---
title: "got this message at the start up"
date: 2010-03-15
forum: General Help
---

### Post by kosaidpo on 2010-03-15
hello guys im new here i jst got and account on here n its still fresh : D

im sorry if its not the perfect place for this kind of issue and tnx

```

there's a problem with server configuration
/usr/lib/libconf2-4/gconf-sanity-check-2 
exit with the stat 256

```

i dont what to do to fix it

---

### Post by dcstar on 2010-03-15
> **kosaidpo said:**
> hello guys im new here i jst got and account on here n its still fresh : D

im sorry if its not the perfect place for this kind of issue and tnx

```

there's a problem with server configuration
/usr/lib/libconf2-4/gconf-sanity-check-2 
exit with the stat 256

```

i dont what to do to fix it

[https://bugs.launchpad.net/ubuntu/+source/gconf/+bug/269215](https://bugs.launchpad.net/ubuntu/+source/gconf/+bug/269215)

---

### Post by kosaidpo on 2010-03-16
thnx dude for your reply but i still have the same error 
i've tried to chmod my /tmp and the /etc/gconf/gconf.xml.system 
and other thing  i found out there but with no succes

---

### Post by kosaidpo on 2010-03-16
up

---

### Post by dcstar on 2010-03-17
> **kosaidpo said:**
> thnx dude for your reply but i still have the same error 
i've tried to chmod my /tmp and the /etc/gconf/gconf.xml.system 
and other thing  i found out there but with no succes

Then add your problem to the bug report and see if the developers can come up with a fix - that is why Launchpad exists.

---

### Post by kosaidpo on 2010-03-17
well first im new to this then i dont kno how to add it plus when i run that file
```

 /usr/lib/libgconf2-4/gconf-sanity-check-2 

```
it gave me this 
```

please contact your admin system to solve this problem
its impossible to open o creat the file NULL
thats means there's a problem in your configuration seen that many programs have to create files in your persoal directory  the error is 
the creation of file /tmp/gconf-test-locking-file-T8DM9U failed 
permission unallowed errno=13
impossible to delete the file NULL bad adresse

```

well this is just a translation from whant i got cus my ubnut run in french so please make that in you consideration


and even i've tried to create that file test on my /tmp still givin  me same error but today after some manipulation when i run 

```
 /usr/lib/libgconf2-4/gconf-sanity-check-2 
```

it gives me this 
```


to poursuit you files that has your setting they 're in use now
and maybe your connected in session from another computer and the other session its using your preference setting
so if you choose to continue you my have some temproraly problems
do you want to continue O/N ??

```

PS:i didnt continue i hit the NO

---

### Post by dcstar on 2010-03-17
> **kosaidpo said:**
> well first im new to this then i dont kno how to add it plus when i run that file
......

Firstly, you do not run that command, the system does.

Secondly, in Launchpad you create an account, go to the bug and use the "Does this bug affect you" tool, then you will be notified if/when it is fixed and the developers will have one more reason to fix it.

---

