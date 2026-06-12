---
title: "change users default home directory?"
date: 2010-11-08
forum: General Help
---

### Post by telefonen on 2010-11-08
Can someone help with how to change when running command "adduser" or "useradd" the placement of the users home directory.
Have tried editing the /etc/default/useradd file with no results.

I want it to be placed in /var/www
And I would also want to know how more folders and files can be created in the home directory automatically.

---

### Post by wojox on 2010-11-08
> **telefonen said:**
> Can someone help with how to change when running command "adduser" or "useradd" the placement of the users home directory.
Have tried editing the /etc/default/useradd file with no results.

I want it to be placed in /var/www
And I would also want to know how more folders and files can be created in the home directory automatically.

You could copy or move the new directory to /var/www/ but that really isn't a wise decision.

Add folders and files just right click in the GUI. Let me know if you want terminal commands. :)

---

### Post by telefonen on 2010-11-08
I meant more this way
how do i change that the /home/"username" folder automatically gets placed in /var/www/"username" 
and when added a new user in his home directory i want three folders called www, dev and www2 be added automatically

---

### Post by SeijiSensei on 2010-11-08
> **telefonen said:**
> I meant more this way
how do i change that the /home/"username" folder automatically gets placed in /var/www/"username" 
and when added a new user in his home directory i want three folders called www, dev and www2 be added automatically

The user's home directory appears in /etc/passwd.  You can edit it manually there.  Or you can use "useradd -b /var/www username" when creating the user.

For your second question, you need to add the www, dev, and www2 to /etc/skel like this:

```

cd /etc/skel
sudo mkdir www dev www2

```

These directories will then be part of the default home directory structure for all new users.

---

### Post by dcstar on 2010-11-09
> **telefonen said:**
> Can someone help with how to change when running command "adduser" or "useradd" the placement of the users home directory.
Have tried editing the /etc/default/useradd file with no results.

I want it to be placed in /var/www
And I would also want to know how more folders and files can be created in the home directory automatically.

/home folders have specific security requirements that may not take kindly to someone mucking around putting them in other system folders with their own security model.

---

### Post by telefonen on 2010-11-09
At work we have an CentOS server with this configuration and I want it to work on my ubuntu machine here at home.
So when typing "adduser test" home directory gets placed in /var/www/html
Isnt it a way to do this in ubuntu?

---

### Post by SeijiSensei on 2010-11-12
> **telefonen said:**
> At work we have an CentOS server with this configuration and I want it to work on my ubuntu machine here at home.
So when typing "adduser test" home directory gets placed in /var/www/html
Isnt it a way to do this in ubuntu?

Look at /etc/adduser.conf and change the DHOME value to /var/www/html.  You'll need to use sudo to edit this file.

---

