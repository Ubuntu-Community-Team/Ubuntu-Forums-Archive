---
title: "Different between the two ways of Disable Ubuntu Root Password"
date: 2010-03-05
forum: General Help
---

### Post by dixcuxx on 2010-03-05
I find out there are two ways to do that:
sudo passwd -l root
sudo usermod -p &#8216;!&#8217; root

What are the different? 
I saw a kubuntu post said:
-l, --lock 
 Lock the named account. This option disables an account by changing the password to a value which matches no possible encrypted value.

I enable and set a root password, I want to return to a "no possible encrypted value" just like the way it was:popcorn:

---

### Post by jmichelsen on 2010-03-05
The /etc/passwd file contains all values pertaining to useraccounts, except when xshadow is enabled (usually is by default) in which the passwords are stored elsewhere.

Using ```
usermod -L
```will do the same thing as both of these other commands you mentioned. They fill an * into the password value in the /etc/passwd file.

So if you are asking which method to use, pick one :) they will do the same thing. You could alternatively go into the /etc/passwd file and put an * in the second block like this:

```
root:x:0:0::/root:/bin/bash
```

and change it to

```
root:*:0:0::/root:/bin/bash
```

hope this helps

---

### Post by dixcuxx on 2010-03-05
> **jmichelsen said:**
> The /etc/passwd file contains all values pertaining to useraccounts, except when xshadow is enabled (usually is by default) in which the passwords are stored elsewhere.

Using ```
usermod -L
```will do the same thing as both of these other commands you mentioned. They fill an * into the password value in the /etc/passwd file.

So if you are asking which method to use, pick one :) they will do the same thing. You could alternatively go into the /etc/passwd file and put an * in the second block like this:

```
root:x:0:0::/root:/bin/bash
```

and change it to

```
root:*:0:0::/root:/bin/bash
```

hope this helps


Thanks. Why would there be two different comments if they do exactly the same thing? :KS

---

### Post by dixcuxx on 2010-03-05
I almost finish my job today ho yeah! US is going to be morning now..hope more people would come to answer my question:D

---

### Post by dixcuxx on 2010-03-05
my question is that professional? Just one human in the world knows about it? LOL:D

---

### Post by jmichelsen on 2010-03-05
Ya know, that's kinda what Linux is all about, having many different ways to do the same thing. The GUI, i.e. Gnome or KDE are just GUI's for command line utilities. Just about everything in Linux has multiple ways to accomplish them.

I would love to see someone else give more info on why/if there are differences with these ways of disabling an account, but I'm not sure the topic is that broad.

---

### Post by sisco311 on 2010-03-05
The passwords are stored in the /etc/shadow file in encrypted format.

The second filed in the file is the hash value. See:
[http://www.cyberciti.biz/faq/understanding-etcshadow-file/](http://www.cyberciti.biz/faq/understanding-etcshadow-file/)

```
passwd -l user
```
or
```
usermod -L user
```
adds a "!" at the beginning of the hash. You can later run:
```
passwd -u user
```
or
```
usermod -U user
```
to unlock the password (remove the leading '!'). in this way you can use the same password as before locking it.

```
usermod -p '!'
```replaces the whole hash with a '!'. So you can't simply unlock the account, you have to set a new password.

---

### Post by jmichelsen on 2010-03-05
Thanks for clearing that up sisco311

---

### Post by dixcuxx on 2010-03-06
> **sisco311 said:**
> The passwords are stored in the /etc/shadow file in encrypted format.

The second filed in the file is the hash value. See:
[http://www.cyberciti.biz/faq/understanding-etcshadow-file/](http://www.cyberciti.biz/faq/understanding-etcshadow-file/)

```
passwd -l user
```
or
```
usermod -L user
```
adds a "!" at the beginning of the hash. You can later run:
```
passwd -u user
```
or
```
usermod -U user
```
to unlock the password (remove the leading '!'). in this way you can use the same password as before locking it.

```
usermod -p '!'
```replaces the whole hash with a '!'. So you can't simply unlock the account, you have to set a new password.

so cool thanksI improve my linux knowledge today:popcorn:

---

