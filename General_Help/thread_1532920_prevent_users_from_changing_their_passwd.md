---
title: "prevent users from changing their passwd"
date: 2010-07-17
forum: General Help
---

### Post by sulekha on 2010-07-17
Hi all,

I use the following method for preventing the users from changing their passwords , is there any other method other than this ?


ls -l /usr/bin/passwd
 -rwsr-xr-x 1 root root 37140 2010-01-26 12:09 /usr/bin/passwd

so we need to remove the suid for that command as follows :- chmod u-s /usr/bin/passwd

 now normal users won't be able to change their own passwords - and only the root user will be able to do it for them.

---

### Post by sisco311 on 2010-07-17
You could set the user's minimum password age to 2^63-1 (~25269512429739111 years):
```
sudo passwd --mindays 9223372036854775807 username
```

Or the maximum password age lower than the minimum password age and the warning and inactivity period to 0.

See:
```

man shadow | less +/"minimum password age"
man passwd | less +/--mindays
```

---

### Post by sulekha on 2010-07-17
[QUOTE=sisco311;9600516]You could set the user's minimum password age to 2^63-1 (~25269512429739111 years):
```
sudo passwd --mindays 9223372036854775807 username
```



 first I re-enabled sticky bit (ubuntu 10.04 machine)
zodiac@gml-admin:~$ ls -l /usr/bin/passwd
-rwsr-xr-x 1 root root 37140 2010-01-26 12:09 /usr/bin/passwd

and then I tried what you have said ( ubuntu 10.04 machine) to get the following result


zodiac@gml-admin:~$ sudo passwd --mindays 9223372036854775807 gmluser
passwd: invalid numeric argument '9223372036854775807'
Usage: passwd [options] [LOGIN]

---

### Post by sisco311 on 2010-07-17
Try a lower value, i.e. 20000 (~54 years). I'm using the 64bit version, I don't know what's the max on a 32bit system.

EDIT: I guess it's 2^31-1(=2147483647) on a 32bit system, but I think it's futile to set it to be higher than 27 years anyway. [http://en.wikipedia.org/wiki/Year_2038_problem](http://en.wikipedia.org/wiki/Year_2038_problem)

---

### Post by sulekha on 2010-07-17
> **sisco311 said:**
> Try a lower value, i.e. 20000 (~54 years). I'm using the 64bit version, I don't know what's the max on a 32bit system.

EDIT: I guess it's 2^31-1(=2147483647) on a 32bit system, but I think it's futile to set it to be higher than 27 years anyway. [http://en.wikipedia.org/wiki/Year_2038_problem](http://en.wikipedia.org/wiki/Year_2038_problem)

but still it is wrong I tried the following on another machine

zodiac@zodioc:~$ sudo passwd --mindays 2147483647 testuser
Password changed.
zodiac@zodioc:~$ su testuser
Password: 
testuser@zodioc:/home/zodiac$ passwd
Changing password for testuser.
(current) UNIX password: 
Enter new UNIX password: 
Retype new UNIX password: 
You must choose a longer password
Enter new UNIX password: 
Retype new UNIX password: 
passwd: password updated successfully

---

