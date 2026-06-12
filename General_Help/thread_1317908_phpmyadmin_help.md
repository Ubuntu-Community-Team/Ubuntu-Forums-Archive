---
title: "phpmyadmin help"
date: 2009-11-07
forum: General Help
---

### Post by LAD29 on 2009-11-07
Hi all,

Not sure if I'm in the right place here but hopefully someone can help or point me in the right direction.

I am wondering if it is possible to show the permissions/privileges of the current user logged into phpmyadmin via a SQL query.

Can anyone help?

Cheers.

---

### Post by indytim on 2009-11-07
Short Answer:

Not easily.


Longer Answer:

I believe that the Ubuntu security is handled exterior to the MySQL server.  I believe you would need to write a php script to read from the security file(s) assuming they are not encrypted.

Your question really has nothing to do with phpMyAdmin.

IndyTim

---

### Post by LAD29 on 2009-11-07
Hi,

Thanks for the reply.  Not sure if I'm reading you wrong, or you're reading me wrong.

I don't mean the ubuntu user account.  I mean the MySQL user that is logged into phpmyadmin.  That's why I was thinking that I must be able to find a way of showing what permissions that MySQL user has on the database it's just connected to via phpmyadmin.

Is that what you meant, am I reading you wrong?

Cheers.

---

### Post by indytim on 2009-11-07
Disconnected...:p

I thought you were referencing the Ubuntu user.  I suspect that the user info is recorded in a session variable once the user is logged into phpMyAdmin.  I can't offer anymore specifics beyond that.  You might want to swing over to phpMyAdmin and post to their boards there for full and authoritative answer.

IndyTim

---

### Post by orlox on 2009-11-07
Your question is actually more of a mysql issue than a phpmyadmin one.

Checking permissions for a particular user who isn't root, is equivalent to checking the grants he has on different tables. Probably this sql query would help:

```

SHOW GRANTS FOR 'yourusername'@'localhost';

```

Where you can switch yourusername with whatever the user you're logged as is called

---

### Post by orlox on 2009-11-07
Actually, it's even easier:

```

SHOW GRANTS FOR CURRENT_USER;

```

That will show the info for the connected user.

---

### Post by LAD29 on 2009-11-07
Thanks guys!

Cheers orlox. When I run that I get the following:

GRANT USAGE ON *.* TO 'xxxxxxxx'@'%' IDENTIFIED BY PASSWORD 'xxxx'
GRANT ALL PRIVILEGES ON `xxx`.* TO 'xxx'@'%'

So I'm guessing that the current user as all privileges turned on for that database.

As an aside, and a cheeky bonus question...

Is there a way to change the current user within phpmyadmin without having to come out?

I ask because, via my host (which uses Plesk control panel)I have to select my database, then in the list of users I have to change the "default user for webadmin" before clicking on the webadmin icon which then opens up phpmyadmin with that user account.

Bit of a chore, having to come out and back in again for each user/database, so would be cool to be able to use SQL commands within phpmyadmin to switch users etc.

Just a thought.

Cheers.

---

### Post by orlox on 2009-11-07
I don't think phpmyadmin has a fast way to switch between users. If for security reasons you can't grant permissions on the user you are actually using to access a particular DB, then I think as a workaround you could just open another browser (besides firefox) and keep in both browsers a session opened with different users.

---

