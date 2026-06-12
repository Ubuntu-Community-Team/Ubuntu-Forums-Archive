---
title: "Sudo: user is not in the sudoers file . This incident will be reported"
date: 2010-03-25
forum: General Help
---

### Post by Benthe1st on 2010-03-25
Hi!

I get this message if i try to use sudo/gksudo. What causes this, how can I solve it? It has been working for years. If i remember correcttly there was a sudo update few days ago, maybe it doesnt work since then, i havent used it in the last few days.

Balazs

---

### Post by uncle-c on 2010-03-25
You have to make sure that you are listed in the /etc/sudoers file along with the command that you are trying to execute as superuser.

Here is an example sudoers file ( just the important bit )

```
# User privilege specification
root	ALL=(ALL) ALL
unclec  ALL=(ALL) ALL
  
davethecat ALL= NOPASSWD: /sbin/fdisk  
 
```

unclec can use sudo to execute all commands as root from any machine but has to supply his password. davethecat can only use sudo to execute fdisk as root and does not need to supply his password to run it. He can also run it from any machine.

---

### Post by wojox on 2010-03-25
It means your not a member of the admin group.

[http://ubuntuforums.org/showpost.php?p=7196198&postcount=5](http://ubuntuforums.org/showpost.php?p=7196198&postcount=5)

---

### Post by Benthe1st on 2010-03-25
> **wojox said:**
> It means your not a member of the admin group.

[http://ubuntuforums.org/showpost.php?p=7196198&postcount=5](http://ubuntuforums.org/showpost.php?p=7196198&postcount=5)

But how it happened? It's not a new ubuntu install. I was memeber of the admin group, I've used sudo several times, my user is the only one on the machine, then how i will add myself to it?

---

### Post by wojox on 2010-03-25
Follow what that link says. You'll have to reboot into recovery mode to edit visudo since you can't sudo. Add your 

```
<userName> ALL=(ALL) ALL
```

---

### Post by Benthe1st on 2010-03-25
Ok, thx, i found it, but still dont understand how it could happen.

---

### Post by philinux on 2010-03-25
> **Benthe1st said:**
> Ok, thx, i found it, but still dont understand how it could happen.

[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

Look under Causes and Symptoms.

---

### Post by Xshady on 2010-03-31
I had the same problem recently, so I tried the solution and it worked, however I never knew that I can login as root without any password when in recovery mode !! I was even able to change my default password, list some confidential files ... I think that's not safe, I share my PC with co-workers !! So how can I please redress that ??

---

### Post by Calash on 2010-03-31
Physical access to a computer is a security risk that no amount of software can bypass.  No matter what you do, somebody sitting in front of the keyboard will be able to find a way around it.


You could remove the recovery entry from GRUB, but then you will not have access to it should something go wrong.  That would be a  grub.cfg edit, I think.

---

### Post by Xshady on 2010-04-02
I have just set a root password :

```
sudo passwd
```

No need for removing anything from GRUB !

Thanks

---

### Post by rajke88 on 2011-06-23
okej i registered my account here, just that i could reply to the this topic.. i dont have that much time, and i have to post mine solution fast here.. this is what helped me.. since i am begginer at linux, i had this problem on my Debian OS .. and this solved it.

on debian i have to go to system/administration/users and gropus
it is still gnome 2 desktop enviroment, and u on ubuntu just tupe in dash users and it will show u this option..

how open it and select user, make it **administrator** and click down on the groups and put him into **root** and **sudo** group, after that just restart PC and login u should be able to use sudo commands from the console

p.s i dont know if u need to put ur self in root group, maybe just sudo is enough, but i did it both... hope i helped beginers here.. cheers! :popcorn:

---

