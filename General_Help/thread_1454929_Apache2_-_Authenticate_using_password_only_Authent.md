---
title: "Apache2 - Authenticate using password only? Authenticate without 'User Name' prompt?"
date: 2010-04-15
forum: General Help
---

### Post by LurkyLou on 2010-04-15
Hi!  I'm trying to password-protect my site, but I want the user to only be prompted for a password (not a user name).  I was playing around with Zubrag's Password_Protect.php
[http://www.zubrag.com/scripts/password-protect.php](http://www.zubrag.com/scripts/password-protect.php)
but it seems to only cover individual pages, not the entire site, like .htaccess does when it's put into httpd.conf.

Another option might be to .htaccess with a guest account but have the word "Guest" appear in the User Name box without the user entering it.  I'm still Googling around trying to figure out how to do this.
Can anyone show me how to do this OR direct me to links?  
Thanks!, LL

---

### Post by Untitled_No4 on 2010-04-15
I'd do it by creating two files.
The first is a login page with a form asking for password only. Once the form is submitted check the password (either from a database, or if you only want only one shared password you can hard code it). If the login is successful store something into your php session such as $_SESSION['login'] = 1 or $_SESSION['user_id'] = $user_id if you actually have users and redirect the users to the homepage or whatever.

The other file is a header/application_top file which will be included at the top of all pages EXCEPT the login page. In the header check that the session variable set in login page exists (e.g. if ($_SESSION['login'])) and if it doesn't redirect the user to the login page.

You will have to start the session on each and single page of the application and so adding it to this header file is the best way to go. 

This is just a basic concept. Have a read about php sessions if you haven't already and also about SQL injections since if your login code is not secure enough people with the right knowledge can fool it into letting them in even without the password if you are using a database for the login info.

And all this was suggested assuming you are working with PHP since you've mentioned a php script in your post.

---

