---
title: "limit user access"
date: 2010-08-13
forum: General Help
---

### Post by watgrad on 2010-08-13
Hi,

I am trying to create limited user accounts for my home computer (for my kids accounts).  I would like to block some programs from running in their account (like firefox, my work email client...etc.).
How to I change their permissions to prevent them from opening/accessing specific programs?

Thanks for any suggestions...

---

### Post by viralmeme on 2010-08-13
> **watgrad said:**
> I would like to block some programs from running in their account (like firefox, my work email client...etc.)

Under Linux files are owned by user:group and marked read, write or executable. Set your account to be a default member of admin and set the users accounts to be members of users. Then restrict the executables to group admin. As in this example, chrome is only executable by root and members of the admin group. Be carefull messing about with file permissions :)

$chown root:admin /path/to/executable
$chmod o-x /path/to/executable

-rwxr-xr--  1 root admin 36245628 2010-08-13 14:11 chromium-browser

---

### Post by watgrad on 2010-08-13
Great - that worked!

Is there a way to then run the applications using sudo from the limited account?  (for those rare occasions when I am working with my kids on a project in their account and we discover we need the internet...)

I attempted to run sudo chromium-browser while logged into their account, the terminal asked for the sudo password but then wouldn't recognize it...

I realize probably it would be better to setup an internet filter - but the procedures I've read for that are very daunting for a ubuntu / command line noob...

Thanks again for any ideas,

---

### Post by Sef on 2010-08-13
> I realize probably it would be better to setup an internet filter - but the procedures I've read for that are very daunting for a ubuntu / command line noob...

I would look at whitelisting the sites that you want the kids to see.  Whitelisting allows only the sites that you choose to view be viewed.

---

### Post by watgrad on 2010-08-13
> **Sef said:**
> I would look at whitelisting the sites that you want the kids to see.  Whitelisting allows only the sites that you choose to view be viewed.

Thanks for the suggestion - ProCon Latte seems to work just fine.

---

### Post by viralmeme on 2010-08-14
> **watgrad said:**
> Is there a way to then run the applications using sudo from the limited account?

Using SUDO

[http://aplawrence.com/Basics/sudo.html](http://aplawrence.com/Basics/sudo.html)


> **watgrad said:**
>  I realize probably it would be better to setup an internet filter 

Setup OpenDNS with family web [I]filter ..

[/I][http://www.opendns.com/](http://www.opendns.com/)

---

