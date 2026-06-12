---
title: "Dummy Mysql setup mistake..help"
date: 2006-04-11
forum: General Help
---

### Post by heislord5 on 2006-04-11
I tried to setup mysql using the official documentation "ubuntu starter guide" page steps.

When I got to:
>  "mysqladmin -u root password db_user_password"

That's exactly what I did...cut and paste...I didn't change the password!!

Now I didn't worry about it then...today I am trying to install vhcs which apparently unstalls, downloads and reinstalls mysql through the automated script you can use from....I don't know where...its on the forums around here in server talk?  Well anyway, used script to auto reinstall mysql...the script asked for new password and old password...I left old password empty because I assumed the old password had not been reused from the old installation  and the script instructions say:

> If you have not changed your MySQL password outside this script, just hit enter.

Well I got this as a result:

> Enter password:
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'

I don't know what that means?  Does this mean my attempt to set the password failed?  How can I set it?

---

### Post by heislord5 on 2006-04-11
never mind.

Got it working with the "can't set the password with mysqladmin :(" thread.

[http://ubuntuforums.org/showthread.php?t=27156&page=2&highlight=mysql+%27Access+denied+user+%27root%27%40%27localhost%27](http://ubuntuforums.org/showthread.php?t=27156&page=2&highlight=mysql+%27Access+denied+user+%27root%27%40%27localhost%27)

---

