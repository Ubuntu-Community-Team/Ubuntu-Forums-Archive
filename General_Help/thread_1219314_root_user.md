---
title: "root user"
date: 2009-07-21
forum: General Help
---

### Post by roc6977 on 2009-07-21
**** how do I get to be root? Thanks

---

### Post by bacil on 2009-07-21
first of all set root password 

```
 sudo passwd 
```

then su to root

```
su -
```

and you are root

---

### Post by mudcat on 2009-07-21
sudo or su - if you have set up the root password

---

### Post by credobyte on 2009-07-21
Enter root:
```
sudo -i
```
Exit root:
```
exit
```

---

### Post by grayn0de on 2009-07-21
This thread explains this well (the appropriate commands, I mean):

[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

---

### Post by bacil on 2009-07-21
this brings up question ... DO you set root password on your boxes ?

i always do, but it is habit from pre-sudo days :))), and you never know when you might need to get in as root

---

### Post by JohnnySage50307 on 2009-07-21
Well, there are three ways, all of which require you to know the root password.
 
1. Login to the system as root
2. Through Terminal/Console, "sudo" gives you the power of root
3. "su -l" will switch your user to root through Terminal/Console
 
Typically, if you have admin privilages or if you set up the system, your password is the root password.  If you do not know the password or lack the permissions, then you shouldn't try to do this--most admins respond by simply deleting your account and resetting the root password.

---

### Post by roc6977 on 2009-07-21
Thanks Bacil!

---

### Post by nothingspecial on 2009-07-21
Read [[COLOR="Magenta"]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=716201")

---

### Post by SuperSonic4 on 2009-07-21
> **bacil said:**
> this brings up question ... DO you set root password on your boxes ?

i always do, but it is habit from pre-sudo days :))), and you never know when you might need to get in as root

I do but that's because arch needs it. Normally I use sudo but frankly being root is so much easier sometimes

---

### Post by sisco311 on 2009-07-21
> **bacil said:**
> this brings up question ... DO you set root password on your boxes ?

i always do, but it is habit from pre-sudo days :))), and you never know when you might need to get in as root

Since the sulogin shipped with Ubuntu is patched to handle disabled root account there is no real need to enable it.

You can *sudo -i* to simulate initial login.

Please read the link posted by [nothingspecial]("http://ubuntuforums.org/member.php?u=491516") and [grayn0de]("http://ubuntuforums.org/member.php?u=876509") and the community doc:[uhelp]community/RootSudo[/uhelp] and try to educate new users to use sudo.  

> **SuperSonic4 said:**
> I do but that's because arch needs it. Normally I use sudo but frankly being root is so much easier sometimes

+1, but i only use it when i have to boot in single user mode.

---

