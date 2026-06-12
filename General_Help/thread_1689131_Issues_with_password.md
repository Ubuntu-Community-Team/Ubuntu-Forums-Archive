---
title: "Issues with password"
date: 2011-02-16
forum: General Help
---

### Post by neokyle on 2011-02-16
Cant seem to use my mysql password, keep getting the error

" Access denied for user 'root'@'localhost' (using password: YES)"

So i tried checking my password using mysql -u root -p and I get the same error as above.

Ive tried accessing mysql with skip grant tables disabling the need for a password so i could reset my root password. After going through the necessary steps I still get the error above when typing my password in for mysql.

I really need some help here, ive been wrapping my brain around this for 2 hours and I cant take it anymore.

---

### Post by An Sanct on 2011-02-16
Are you trying to access an user account or root? (the root password was set while installaling)

---

### Post by neokyle on 2011-02-16
root, using the root password I entered upon setup.

I know not to use root, Im using it until everything is setup.

---

### Post by An Sanct on 2011-02-16
root for MySQL? or the computer?

Hm :) I'm confused now ... so ill just point you to the solution for MySQL root password changing.
look [here]("http://ubuntu.flowconsult.at/en/mysql-set-change-reset-root-password/").

That should do it ... if yes, please mark the thread as solved.

---

### Post by neokyle on 2011-02-16
> **An Sanct said:**
> root for MySQL? or the computer?

Hm :) I'm confused now ... so ill just point you to the solution for MySQL root password changing.
look [here]("http://ubuntu.flowconsult.at/en/mysql-set-change-reset-root-password/").

That should do it ... if yes, please mark the thread as solved.

sorry but ive tried that method about 5 times after multiple reinstalls. After doing it and checking to see if the password worked I get the error i posted in my first post.

---

