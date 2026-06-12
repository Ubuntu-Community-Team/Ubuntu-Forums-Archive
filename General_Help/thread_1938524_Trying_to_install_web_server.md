---
title: "Trying to install web server"
date: 2012-03-09
forum: General Help
---

### Post by Somiac on 2012-03-09
Hey all, I'm not sure which area to place this topic...

I'm following the directions to install a webserver on ubuntu at this site here - [http://www.howtoforge.com/ubuntu_lamp_for_newbies](http://www.howtoforge.com/ubuntu_lamp_for_newbies)

And at the point of doing 

> 
Step 3. This is where things may start to get tricky. Begin by typing the following into Terminal:

mysql -u root

Following that copy/paste this line:

mysql> SET PASSWORD FOR 'root'@'localhost' = PASSWORD('yourpassword');

(Make sure to change yourpassword to a password of your choice.) 


I get lost, it keeps saying an error has occured. I've tried both commands seperately and together such as this

> meta@ubuntu:~$ mysql -u root
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)
meta@ubuntu:~$ mysql> SET PASSWORD FOR 'root'@'localhost' = PASSWORD('mysqlpw');
bash: syntax error near unexpected token `('

but it keeps bring up these errors, unsure of how to fix it. Thanks!

---

### Post by Iowan on 2012-03-09
**mysql -u root** *should* have gotten you logged in - the **mysql>** should be the prompt.
> meta@ubuntu:~$ [COLOR="Red"]mysql> [/COLOR]SET PASSWORD FOR 'root'@'localhost' = PASSWORD('mysqlpw');
You'll notice you *seem* to have two prompts. Put bluntly, this line should have been entered at the mysql prompt - not at the bash (CLI) prompt - thus the error message.

Just in case the password was accepted earlier, try:
**mysql -u root -p**
Enter the password at the prompt. 
I found a guide to resetting a mySQL root password at:
[http://www.cyberciti.biz/tips/recover-mysql-root-password.html](http://www.cyberciti.biz/tips/recover-mysql-root-password.html)

---

