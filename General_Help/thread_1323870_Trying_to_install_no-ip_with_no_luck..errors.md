---
title: "Trying to install no-ip with no luck..errors"
date: 2009-11-12
forum: General Help
---

### Post by nicklausmichael on 2009-11-12
```
c0ld@c0ld-laptop:~/noip/noip-2.1.9-1$ sudo make install
if [ ! -d /usr/local/bin ]; then mkdir -p /usr/local/bin;fi
if [ ! -d /usr/local/etc ]; then mkdir -p /usr/local/etc;fi
cp noip2 /usr/local/bin/noip2
/usr/local/bin/noip2 -C -c /tmp/no-ip2.conf

Auto configuration for Linux client of no-ip.com.

Please enter the login/email string for no-ip.com  nicknoip@hotmail.com
Please enter the password for user 'nicknoip@hotmail.com'  ******

No hosts are available for this user.
Go to www.no-ip.com and create some!

Configuration file can NOT be created.

mv /tmp/no-ip2.conf /usr/local/etc/no-ip2.conf
mv: cannot stat `/tmp/no-ip2.conf': No such file or directory
make: *** [install] Error 1
c0ld@c0ld-laptop:~/noip/noip-2.1.9-1$
```Please help..lol

---

### Post by hal10000 on 2009-11-12
Activate your universe repository and install it with your package manager

---

### Post by nicklausmichael on 2009-11-12
Did that and still get the same response...

---

### Post by t4thfavor on 2009-11-12
switch to root, or change the config manually. It appears that the file cannot be modified by the regular user account you are running as. Even if you are using sudo, the script could be running some task (like mv or cp) as the regular user account.


Or this could have something to do with it.

"Go to [www.no-ip.com](www.no-ip.com) and create some"

---

### Post by nicklausmichael on 2009-11-12
> **t4thfavor said:**
> switch to root, or change the config manually. It appears that the file cannot be modified by the regular user account you are running as. Even if you are using sudo, the script could be running some task (like mv or cp) as the regular user account.


Or this could have something to do with it.

"Go to [www.no-ip.com]("http://www.no-ip.com") and create some"
Yah Ive gone to no-ip.com and I have stuff on my account... but Ill try to switch from terminal to root and see what happens...


**************************************************************************************** 
Instead of double posting Ill just edit this one.. I tryed what you suggested and here is what I got

```

root@c0ld-laptop:/home/c0ld# cd /home/c0ld/noip/noip-2.1.9-1
root@c0ld-laptop:/home/c0ld/noip/noip-2.1.9-1# make install
if [ ! -d /usr/local/bin ]; then mkdir -p /usr/local/bin;fi
if [ ! -d /usr/local/etc ]; then mkdir -p /usr/local/etc;fi
cp noip2 /usr/local/bin/noip2
/usr/local/bin/noip2 -C -c /tmp/no-ip2.conf

Auto configuration for Linux client of no-ip.com.

Please enter the login/email string for no-ip.com  nicknoip@hotmail.com
Please enter the password for user 'nicknoip@hotmail.com'  ******

No hosts are available for this user.
Go to www.no-ip.com and create some!

Configuration file can NOT be created.

mv /tmp/no-ip2.conf /usr/local/etc/no-ip2.conf
mv: cannot stat `/tmp/no-ip2.conf': No such file or directory
make: *** [install] Error 1
root@c0ld-laptop:/home/c0ld/noip/noip-2.1.9-1# 

```

---

