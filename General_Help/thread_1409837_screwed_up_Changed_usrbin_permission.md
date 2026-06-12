---
title: "screwed up??? Changed /usr/bin permission"
date: 2010-02-18
forum: General Help
---

### Post by sptrsn on 2010-02-18
I was trying to follow the ultimate server instructions [http://nanotux.com/blog/the-ultimate-server](http://nanotux.com/blog/the-ultimate-server) and got a permission error when trying to install mysql. 
so I did a chmod 666 /usr/bin.

Now I have no permission to do anything. 
Any bright ideas?

---

### Post by iponeverything on 2010-02-18
do:

```
sudo chmod 755 /usr/bin


```

---

### Post by r_s on 2010-02-18
you can change it just change to root user mode.

---

### Post by sptrsn on 2010-02-18
I get Permission denied.
How can I change to root user mode?
(also per the guide it's 8.04)

update:
> sudo su gives me a "permission" denied as well. 
I think that's how to change to root user mode.

---

### Post by r_s on 2010-02-18
(su -  ) and then enter the root password

---

### Post by sisco311 on 2010-02-18
Boot in the *Recovery Mode* or boot a Live CD to restore the permissions.

Did you change the permissions recursively or just the permissions of the /usr/bin directory?

---

### Post by rnerwein on 2010-02-18
hi
be careful there are a couple of s-bit commands in there !
ciao

---

### Post by sptrsn on 2010-02-18
Well...long story short. I rebuilt it. 

I booted in recovery, reset the root password, deleted and recreated the user. no joy.
Even created a new user. Couldn't even log into the system anymore. 

So I rebuilt. This time using server, which surprisingly was quite a bit easier.

Thanks for all the help.

---

