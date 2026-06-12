---
title: "Removing single user from gdm"
date: 2010-09-18
forum: General Help
---

### Post by TheWeakSleep on 2010-09-18
I have a quick question that I haven't been able to find an answer for so far. Is it possible to 'hide' a user from the user list in gdm? Note that I don't want to remove it entirely, I just want a user that you can only get into by clicking 'other', entering your name and password.

Can anybody help me?

---

### Post by sisco311 on 2010-09-18
Yes. [noparse]:)[/noparse]

Edit the /etc/gdm/gdm.schemas file:
```
gksu gedit /etc/gdm/gdm.schemas
```

Find the *Exclude* section:
```

...
    <schema>
      <key>greeter/Exclude</key>
      <signature>s</signature>
      <default>bin,root,daemon,adm,lp,sync,shutdown,halt,mail,news,uucp,operator,nobody,nobody4,noaccess,postgres,pvm,rpm,nfsnobody,pcap</default>
    </schema>
...

```
and add the user to the list:
```

...
    <schema>
      <key>greeter/Exclude</key>
      <signature>s</signature>
      <default>**username,**bin,root,daemon,adm,lp,sync,shutdown,halt,mail,news,uucp,operator,nobody,nobody4,noaccess,postgres,pvm,rpm,nfsnobody,pcap</default>
    </schema>
...

```
where **username** is the login name of the user.

---

### Post by TheWeakSleep on 2010-09-18
Thank you so much : )

solved!

---

