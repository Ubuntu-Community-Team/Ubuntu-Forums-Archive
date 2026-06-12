---
title: "Problem adding LDAP user"
date: 2010-07-01
forum: General Help
---

### Post by zaphod777 on 2010-07-01
I followed this guide 
[https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html](https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html)

but when I use the ldapscripts to add a user
```
ldapadduser john media
```

I get
```
root@ldap1:~# ldapadduser john media
Successfully added user john to LDAP


```

But then it just hangs and I have to hit CTRL-C and add the user manually to the group.

Any Ideas?

---

### Post by zaphod777 on 2010-07-05
bumpidty bump.

---

### Post by Josejulio on 2010-07-06
I have that problem also...

---

### Post by zaphod777 on 2010-07-07
I just filed a bug you should say it effects you too.

[https://bugs.launchpad.net/ubuntu/+source/openldap/+bug/602540](https://bugs.launchpad.net/ubuntu/+source/openldap/+bug/602540)

---

### Post by CatWeazel67 on 2010-07-30
I've just hit this to. Did you resolve the problem ?

---

### Post by tsmets on 2010-08-10
It seems from [Bug report]("https://bugs.launchpad.net/ubuntu/+source/openldap/+bug/602540") that the issue is now solved !

<snip>
This bug was fixed in the package ldapscripts - 1.9.0-2ubuntu1
</snip>
and a few lines later :

Changed in ldapscripts (Ubuntu):
**status:**	 Confirmed &#8594; Fix Released

I believe it is just a matter of waiting that the fix is made available on all the mirrors :)

\T,

ps : when I killed the process (we spell "georges" with an "s" in French):
> 
tsmets@ubuntu-server-LTS10:~$ sudo ldapadduser georges example
Successfully added user georges to LDAP

^C

I could change his password afterwards without having to recreate the user .... !
I dunno how much this differ from the initial issue ? ? ?

---

### Post by jetole on 2010-09-23
If I understand the bug report correctly, this will be fixed in maverick and not lucid. In order to fix it in lucid ( 10.04 ), you should edit /etc/ldapscripts/ldapscripts.conf and when you see a line that says:

**PASSWORDGEN="cat /dev/random | LC_ALL=C tr -dc 'a-zA-Z0-9' | head -c8"**

you should change that to be:

**PASSWORDGEN="cat /dev/urandom | LC_ALL=C tr -dc 'a-zA-Z0-9' | head -c8"**

Notice it's now using /dev/urandom instead of /dev/random. Though this does not create passwords which are _as_ random as the original, it seems to solve the original problem which is caused by a lack of entropy.

---

