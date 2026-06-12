---
title: "Passwords"
date: 2011-09-07
forum: General Help
---

### Post by Gwaro on 2011-09-07
I recently changed my user password.This i had selected for the option of the computer generating the password for me.Problem is i copied down only seven characters of the password implying that i dont know what my password is!is there  a way i can reset the password because i am unable to have root privileges,log into my account after a logo ff or after hibernation!

---

### Post by haqking on 2011-09-07
> **Gwaro said:**
> I recently changed my user password.This i had selected for the option of the computer generating the password for me.Problem is i copied down only seven characters of the password implying that i dont know what my password is!is there  a way i can reset the password because i am unable to have root privileges,log into my account after a logo ff or after hibernation!

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

Should help you if you dont have another admin account available

---

### Post by nothingspecial on 2011-09-07
Reboot

Hold down shift

Select recovery mode

Boot a root shell

type

```
passwd [COLOR="Red"]username[/COLOR]
```

(change username for your username)

Choose a new password

Don't worry about all the other stuff (telephone number or whatever), just enter through it.

Type exit

---

### Post by Gwaro on 2011-09-07
It worked.Thanks

---

### Post by haqking on 2011-09-07
> **Gwaro said:**
> It worked.Thanks

cool.

mark the thread as solved using thread tools for the benefit of others.

cheers

---

