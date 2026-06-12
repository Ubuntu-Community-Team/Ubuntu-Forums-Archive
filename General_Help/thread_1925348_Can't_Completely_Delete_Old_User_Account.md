---
title: "Can't Completely Delete Old User Account?"
date: 2012-02-14
forum: General Help
---

### Post by 2CV67 on 2012-02-14
I added a 'Visitor' account in Lubuntu 11.10, for occasional family use where they might want to keep data, which would not be the case for 'Guest session' users, I think.

This account works OK, but threw up a long list of 'permission denied' error messages every time I ran Grsync, even though there is currently nothing stored there.

I thought I would try deleting the account, but when I do so, via Menu > System Tools > Users & Groups, the name 'Visitor' stays visible there.
And visible at the login screen, though trying to login to Visitor leads nowhere.

The /home/Visitor file has gone.

I expected & still expect to be able to completely remove all trace of any account from my PC.

How should I do that?

Thanks!

---

### Post by Vishnu V on 2012-02-14
Try this command to delete user named Visitor
```

sudo userdel -rf  Visitor

```

---

### Post by hildenbrandsteven on 2012-02-14
And make sure all the data is gone from the home folder...

sudo ls /home
sudo rm -rf /home/visitor

---

### Post by 2CV67 on 2012-02-14
```
sudo ls /home
``` > shows only me.

```
sudo userdel -rf  Visitor
``` > 'user Visitor does not exist'

I tried Catfish search tool with 'visitor' & it threw up the following:

[ATTACH]212725[/ATTACH]

I deleted the entry at /var/lib/AccountsService/users > no change, Visitor is still in login screen & in Users & Groups...

I don't understand the various python references, but I don't think they are related to my Visitor, are they?

---

### Post by Vishnu V on 2012-02-14
Account name is case sensitive and please use 
```

sudo userdel -rf  username

```

There is one more chance your username may not be Visitor, to find username 
(Please use capital or small V according to ur username)
```

cat /etc/passwd | grep 'Visitor'

```
If it returns something then it is of the form
```

username:uid:gid:User Info:home directory:default login shell

```
May your actual name is visitor (User Info)
Now try to remove user using
```

sudo userdel -rf  username

```

---

### Post by 2CV67 on 2012-02-15
Thanks, Vishnu V for your suggestions.

Looks a bit confusing to me, but the following has finally removed Visitor/visitor from Users & Groups and also Visitor from the login screen:

```
chris@Acer-desk:~$ cat /etc/passwd | grep 'Visitor'
visitor:x:1001:1001:Visitor,,,,:/home/visitor:/bin/bash
chris@Acer-desk:~$ sudo userdel -rf  Visitor
[sudo] password for chris: 
userdel: user 'Visitor' does not exist
chris@Acer-desk:~$ sudo userdel -rf  visitor
userdel: warning: can't remove /var/mail/visitor: No such file or directory
userdel: visitor home directory (/home/visitor) not found
chris@Acer-desk:~$
```

Thanks again!

---

