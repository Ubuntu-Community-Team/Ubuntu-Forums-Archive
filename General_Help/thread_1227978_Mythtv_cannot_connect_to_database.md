---
title: "Mythtv cannot connect to database"
date: 2009-07-31
forum: General Help
---

### Post by uberanalog on 2009-07-31
I have installed the Mythtv package on my fresh Jaunty install. I get through the setup fine. When I start the frontend I select my language setup my database settings I set durring setup then I am presented with the message "cannot connect to database". Can anybody shed some light on what might be going on here?

---

### Post by CrusaderAD on 2009-07-31
Did you make the database in mysql and give it a username and password to use?
[http://www.mythtv.org/docs/mythtv-HOWTO-6.html#ss6.2]("http://www.mythtv.org/docs/mythtv-HOWTO-6.html#ss6.2")

---

### Post by uberanalog on 2009-08-10
When I attempt to do anything with mysql, for example, if I type mysql in terminal and press enter I get the following:
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password no).

What am I doing wrong here?

Also, when I restart mysql it says both stopping and starting mysql fails.  Why would this be happening?
[FONT=monospace][/FONT]

---

### Post by rajeev1204 on 2009-08-10
> **uberanalog said:**
> I have installed the Mythtv package on my fresh Jaunty install. I get through the setup fine. When I start the frontend I select my language setup my database settings I set durring setup then I am presented with the message "cannot connect to database". Can anybody shed some light on what might be going on here?


This happens because mysql was not installed and run before mythtv install.

Remove mythtv and reinstall mysql ,then give a password for the root password when it asks you to.then reinstall mythtv again

Then run mythtv-setup and it should work fine.

Frankly,i suggest you use tvtime for watching television.

Why the hell should i need to run some 'database' or whatever you call it to watch a TV.

TVtime sets up in just 5 min compared to that beast called mythtv.Unless you want to record programmes(which i thought i might want to but i never did) tv time is superb.

---

