---
title: "Help with phpMyAdmin"
date: 2011-08-24
forum: General Help
---

### Post by rdouglasj on 2011-08-24
I have LAMP installed on Ubuntu 10.04.  I just installed phpMyAdmin.  I'm working on setting up a development environment.

I can view the virtual server ok in Firefox with [http://localhost/phpMyAdmin](http://localhost/phpMyAdmin)

If I open a development application in another window of Firefox using [http://localhost](http://localhost) the application opens OK. It creates a PHP5 $_SESSION id and my browser accepts cookies.

If I close the browser instance that displayed phpMyAdmin
and then...
with the development application still open in another instance of Firefox...
I open another browser instance and try to re-open [http://localhost/phpMyAdmin](http://localhost/phpMyAdmin) 
I get the error message:

    Not Found
    The requested URL /phpMyAdmin was not found on this server.
    Apache/2.2.14 (Ubuntu) Server at localhost Port 80

I have to close all instances of Firefox, destroying the $_SESSION, before phpMyAdmin will open up again using [http://localhost/phpMyAdmin](http://localhost/phpMyAdmin)

Also, my application creates tables prior to login that display OK in phpMyAdmin,
but tables created by the application after login do not display in phpMyAdmin.
My application has a built in query tool, and I can manipulate all of the tables,
so I know the tables exist, but phpMyAdmin cannot see them all.
If I then create a table using phpMyAdmin I can see it there, but not in my application.

I need some help dianosing and fixing the problem.  I think it might be a configuration problem with PHP5, Apache and MySQL, because of the way Firefox is behaving, or possibly a file permissions issue in Ubuntu, but I don't know.

Any suggestions?  I'd be happy to provide any config files if you think you can spot the problem.

---

