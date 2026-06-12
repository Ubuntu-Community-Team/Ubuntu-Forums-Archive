---
title: "Group and User Lists"
date: 2012-09-09
forum: General Help
---

### Post by Jorel on 2012-09-09
Hi guys,,

is there a way to see the users and group and to which group those users are into and also the passwords they have on my Ubuntu server?

Thanks in advance.

---

### Post by codemaniac on 2012-09-09
> **Jorel said:**
> Hi guys,,

is there a way to see the users and group and to which group those users are into and also the passwords they have on my Ubuntu server?

Thanks in advance.

The below will list all the groups, including ones used only by the system.

```
cat /etc/group
```

Below will list all the groups of which the current user is a member .
```
groups
```

---

### Post by Jorel on 2012-09-09
Hi codemaniac,

I saw now the groups and the users that i made, but is there also a way to see their current password or a way to edit the password?

Thanks.

---

### Post by satyamM on 2012-09-09
> **Jorel said:**
> 
I saw now the groups and the users that i made, but is there also a way to see their current password or a way to edit the password?



Passwords are stored in /etc/shadow....you can do [HTML]sudo cat /etc/shadow[/HTML] to see passwords, but I doubt you can change passwords unless you are root. Plus passwords in shadow file are encrypted, you cant see actual passwords...some hashing technique is used to encrypt passwords (might be md5 hashing)..


Regards.
Satyam M.

---

### Post by Jorel on 2012-09-09
Hi satyamM,

yes im using the root and im the only one who's using the server,,, but most of the users are requesting to change their passwords and the group they are into now thats why i asked for that... but when i type cat /etc/shadow i just saw a bunch of alphanumeric codes, and i cant even see my own password there ;) 

Thanks.

---

### Post by zombifier25 on 2012-09-09
> **Jorel said:**
> Hi satyamM,

yes im using the root and im the only one who's using the server,,, but most of the users are requesting to change their passwords and the group they are into now thats why i asked for that... but when i type cat /etc/shadow i just saw a bunch of alphanumeric codes, and i cant even see my own password there ;) 

Thanks.

Like what he said, the password in /etc/shadow is encrypted. If you want to change the password of a certain user, use this command:
```
passwd username
```

---

### Post by codemaniac on 2012-09-09
> **Jorel said:**
> Hi codemaniac,

I saw now the groups and the users that i made, but is there also a way to see their current password or a way to edit the password?

Thanks.

You cannot decipher other users password, even as root.All you can do is change the password .

```
man passwd
```

---

### Post by Jorel on 2012-09-09
> **zombifier25 said:**
> Like what he said, the password in /etc/shadow is encrypted. If you want to change the password of a certain user, use this command:
```
passwd username
```

thanks for the info... i can now change passwords..

Thanks for helping guys...

---

