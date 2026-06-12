---
title: "[SOLVED] How do execute admin commands in non admin account?"
date: 2006-03-03
forum: General Help
---

### Post by cgborkgb on 2006-03-03
Hi.  After installing Ubuntu, I created a new user with full privileges and stripped the administrative priveleges from the original user (setup during install).  How can I get the ability to execute administrative commands in the non admin user account?  I try 'su' and 'sudo' and enter the admin's password, but it doesn't work.  I've been told that I need to add the user to the admin's wheel, but I haven't been able to find out how to do that from Google search (the only thing that was relevant was for UNIX, which did not work in Ubuntu).

Thanks for reading :)

---

### Post by Q4U on 2006-03-03
You have to use sudo and type the user's password, not the administrator's password. Q4U

---

### Post by hw-tph on 2006-03-03
Edit /etc/group and add the new user account to the admin line. This is a comma separated list so you can add more than one: 

```
admin:x:106:hakan,anders,bo
```

This will let your user use sudo.


Håkan

---

### Post by cgborkgb on 2006-03-04
Sweet.  Thanks Håkan.

---

### Post by jtann on 2007-10-23
i have the same problem here if i do this command says no write permisson for file

---

### Post by jtann on 2007-10-23
back up my problem is neither of my two users have admin right how do i fix this.

---

### Post by zaphod777 on 2007-10-23
you need to issue the following command from the terminal

sudo gedit etc/group

i should now open it with admin privilages and you can save it.

---

### Post by jtann on 2007-10-23
i got the file open but it shows to be blank

---

### Post by aysiu on 2007-10-23
That's because there's a missing slash in there. The correct command is: ```
gksudo gedit /etc/group
``` Of course, if you're not in the *admin* group already, you won't be able to use *gksudo* or *sudo*.

Here are instructions for that case:
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

---

### Post by jtann on 2007-10-23
yes thank you both very much got it all back :):)

---

### Post by zaphod777 on 2007-10-23
good to hear.

---

### Post by BLTicklemonster on 2007-11-26
> **aysiu said:**
> That's because there's a missing slash in there. The correct command is: ```
gksudo gedit /etc/group
``` Of course, if you're not in the *admin* group already, you won't be able to use *gksudo* or *sudo*.

Here are instructions for that case:
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

Excellent. My daughter's up in North Carolina, and somehow she couldn't do any admin stuff. adduser did the trick.
Aysiu, you rock.

---

