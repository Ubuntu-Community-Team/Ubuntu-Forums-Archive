---
title: "Reset password"
date: 2012-01-23
forum: General Help
---

### Post by zephonic on 2012-01-23
Hello, noob here.

Am on Ubuntu 11.10 and somehow it says my password is incorrect every time I try to authenticate something. Updates, new apps or whatever, nothing goes because I keep getting the password wrong.

I gave up trying to guess and just want to reset it so I have access again. Is this possible and if yes, how to go about it?

---

### Post by papibe on 2012-01-23
So you are able to login, but not run sudo?
Is this a Wubu or a regular install?

Regards.

---

### Post by zephonic on 2012-01-24
It is a regular install.

I disabled password login, so I can use the machine for generic stuff, but as soon as admin level action is required I'm lost in the woods.

I'm sure I know the password, but for some reason I get it wrong. Maybe a typo when I set it, but not likely. Who knows? Question is:

how to get rid of it, short of  a complete reinstall?

---

### Post by papibe on 2012-01-24
Boot into 'recovery mode', then choose to get a root prompt. Once there run:
```
passwd your_user
```
And set your password to whatever you want. To restart your machine:
```
reboot
```
Hope it helps.
Regards.

---

### Post by zephonic on 2012-01-25
Thanks, Papibe. I did get there, but when I changed my password I got something along the lines of "manipulation error - password unchanged". :confused:

So no dice. Yet.

---

### Post by zephonic on 2012-01-25
actual msg is

>  

passwd: Authentication token manipulation error
passwd: password unchanged



---

### Post by papibe on 2012-01-25
Have you manually edit the file /etc/passwd by any chance? What it could be happening is inconsistency between /etc/passwd and /etc/shadow.

Could you post the result of these two commands replacing 'youruser' with your actual username?
```
sudo awk -F: '/youruser/ {print $1}' /etc/passwd

sudo awk -F: '/youruser/ {print $1}' /etc/shadow
```
Regards.

---

