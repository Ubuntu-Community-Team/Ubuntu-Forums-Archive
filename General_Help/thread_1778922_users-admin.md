---
title: "users-admin"
date: 2011-06-09
forum: General Help
---

### Post by 1devils1 on 2011-06-09
Long story short,

Been trying to share a folder from my machine for about 6 months on and off

Hit it hard today and searched for about 2 hours trying different things.

I can't run System>Administration>Users and groups

I get 

The configuration could not be loaded - An unknown error occurred.

After reading a load of stuff i did not really understand I tried to run users-admin from the terminal 

I get the following error

(users-admin:2069): Liboobs-WARNING **: There was an unknown error communicating with the backends: Cannot launch daemon, file not found or permissions invalid


I've searched google for that error and can find only one and it's in Spanish - Ran it through a translator and that makes no sense.

Ubuntu 10.04 LTS - the Lucid Lynx

Any idea's?

Thanks

---

### Post by ruffEdgz on 2011-06-09
Can you run the following commands and reply back to this post with your findings:
```

ll /usr/lib/liboobs-1.so.5.0.0 

```
Thanks.

---

### Post by 1devils1 on 2011-06-09
ls: cannot access /usr/lib/liboobs-1.so.5.0.0: No such file or directory

There is a file called liboobs-1.so.4.0.0

That gives me

-rw-r--r-- 1 root root 153500 2010-03-30 04:33 /usr/lib/liboobs-1.so.4.0.0


I downloaded and installed liboobs-1.so.5.0.0

Results in

-rw-r--r-- 1 root root 153460 2010-09-03 15:49 /usr/lib/liboobs-1.so.5.0.0


Cheers

Paul

---

### Post by ruffEdgz on 2011-06-10
After downloading the new liboobs-1.so.5.0.0, did that help?

The error you gave from above:
> 
(users-admin:2069): Liboobs-WARNING **: There was an unknown error communicating with the backends: Cannot launch daemon, file not found or permissions invalid

Sounded like it needed that file which you had but the older version. Let us know the result of getting into users-admin

---

### Post by 1devils1 on 2011-06-10
No - That did not work.

users-admin

(users-admin:20221): Liboobs-WARNING **: There was an unknown error communicating with the backends: Cannot launch daemon, file not found or permissions invalid

Get the error 

The configuration could not be loaded - An unknown error occurred.

When I try to open users & groups 


Thanks

---

### Post by ruffEdgz on 2011-06-10
Since I don't have this issue plus I have never seen it before, one solution could be to 'reinstall' the package *gnome-system-tools*. 

[http://packages.ubuntu.com/lucid/i386/gnome-system-tools/filelist](http://packages.ubuntu.com/lucid/i386/gnome-system-tools/filelist)

I know how to do this in aptitude:
```

sudo aptitude reinstall gnome-system-tools

```
or do the apt-get command for reinstall:
```

sudo apt-get install --reinstall gnome-system-tools

```
This could help but I can't guaranty it will. It doesn't hurt to try and reinstall to take that part out of the equation.

---

### Post by 1devils1 on 2011-06-10
Thanks for trying to help.

This has not worked.

I'm going to try an upgrade to version 11.

---

