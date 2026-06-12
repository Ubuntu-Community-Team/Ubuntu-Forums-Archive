---
title: "Setting up MySQL"
date: 2006-03-12
forum: General Help
---

### Post by Tim Thumb on 2006-03-12
I've been going through setting up the AMP part of LAMP using [this wiki]("https://wiki.ubuntu.com/ApacheMySQLPHP?highlight=%28apache%29"). Everything seems to have installed correctly and appears to run fine, but I now have no idea of what to do next to set up MySQL.

Do I need to register a host or a database or do something with passwords first? Do I do it all from the command line or is there an app for this kind of thing? I really haven't got a clue at this stage and would appreciate someone's help.

---

### Post by Koybe on 2006-03-12
Use this command to set root password for mysql :
```
mysqladmin -u root password 'your_password'
```
then log in :
```
mysql -u root -p
```

Gl ;)

---

### Post by Tim Thumb on 2006-03-12
Thanks for your reply but this is the error I get:

```
tim@ubuntu:~$ mysqladmin -u root password 'my_password'
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user: 'root@localhost' (Using password: NO)'
tim@ubuntu:~$

```

---

### Post by lamego on 2006-03-12
That means you have already defined a root password for mysql...

---

### Post by l.tambiah on 2006-03-12
Hi Tim,

Hope you have got around your issue, but if you haven't then i suggest you remove the mysql installation. Then re-install the mysql installation and then open a terminal and do the following to set your password before doing anything else(without the dollar).

[I]$ mysqladmin -u root password yourPassword
[/I] 
Where "yourPassword" is the password you choose for root access.

Try the above, and see if that works for you, if you get any problems give us a shout.

---

### Post by Tim Thumb on 2006-03-13
I've tried the uninstall/reinstall and then this:

```
tim@ubuntu:~$ mysqladmin -u root password myPassword
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user: 'root@localhost' (Using password: NO)'

```

Obviously something to do with this root password but it's got me baffled.

---

### Post by adamkane on 2006-03-13
You probably have root access, and a password isn't necessary. Access is limited to the local machine. 

Install mysql-administrator or phpmyadmin. Open up mysql-administrator or phpmyadmin, and log in to mysql as root with no password, and add a new account while you are in there.

Access phpmyadmin this way:
[http://localhost/phpmyadmin/](http://localhost/phpmyadmin/)

---

### Post by Tim Thumb on 2006-03-13
I tried MySQL Administrator like this:

Server Hostname: localhost
Port: 3306
Username: root
Password: <left blank>

Error message: 

Could not connect to host 'localhost'.
MySQL error Nr. 1045
Access denied for user: 'root@localhost' (using password: NO)

Clicking the ping button didn't throw up anything I understand but the ping seemed to be working fine.

I really appreciate everyone's help here.

---

### Post by l.tambiah on 2006-03-13
This is strange, i use mysql all the time and never had this issue. If you can bear with me, as im at work we will get this sorted out for you. Ill post a fix for you in next few hours, i hope...

---

### Post by l.tambiah on 2006-03-13
In meantime try the command:

sudo mysql -u

and use your root password.

If this lets you in you then need to set your password like thus:-

mysql> *SET PASSWORD = PASSWORD('[I]your password*')

[/I]This will set your password for root access.

Next time you now log in from terminal you can use the password you have just set. I.e

$ mysql -u root -p

and enter your pasword at password prompt.

---

### Post by Tim Thumb on 2006-03-13
[QUOTE=l.tambiah]In meantime try the command:

sudo mysql -u

and use your root password.
[/QUOTE]

Gave me:

```
tim@ubuntu:~$ sudo mysql -u
Password:
mysql: option '-u' requires an argument
tim@ubuntu:~$ 
```

I think I need to backtrack a little. When you say the root password, I'm not sure what this is. I've only very recently installed ubuntu and as far as I can remember the only password I've set along the way is the one I use with my username - tim. I'm right in thinking root is a completely different thing? And therefore I'm fairly sure I haven't set a password for root.

>  i use mysql all the time

Me too on Windows and I'm determined to get it working on my ubuntu install too :)

---

### Post by Wide on 2006-03-13
Try this to reset your root password, worked fine for me


look here
[http://dev.mysql.com/doc/refman/4.1/en/resetting-permissions.html](http://dev.mysql.com/doc/refman/4.1/en/resetting-permissions.html)


This also
[http://www.megalinux.net/archives/000183.html](http://www.megalinux.net/archives/000183.html)


> If you have set a root password, but forgot what it was, you can set a new password with the following procedure:
1. Take down the mysqld server by sending a kill (not kill-9) to the mysqld server. The pid is stored in a `.pid' file, which is normally in the MySQL database directory:
shell> kill `cat /mysql-data-directory/hostname.pid`
You must be either the Unix root user or the same user mysqld runs as to do this.

2. Restart mysqld with the --skip-grant-tables option.

3. Set a new password with the mysqladmin password command:
shell> mysqladmin -u root password 'mynewpassword'

4. Now you can either stop mysqld and restart it normally, or just load the privilege tables with:
shell> mysqladmin -h hostname flush-privileges

5. After this, you should be able to connect using the new password.

Alternatively, you can set the new password using the mysql client:

1. Take down and restart mysqld with the --skip-grant-tables option as described above.

2. Connect to the mysqld server with:
shell> mysql -u root mysql

3. Issue the following commands in the mysql client:
mysql> UPDATE user SET Password=PASSWORD('mynewpassword') WHERE User='root';
mysql> FLUSH PRIVILEGES;

4. After this, you should be able to connect using the new password.

5. You can now stop mysqld and restart it normally.

---

### Post by Tim Thumb on 2006-03-13
Cracked it :-D 

Before going through Wide's method I thought I'd just run through everything again. It seems I must have set a password for root in the original set up process. Using this with root as the username got me in.

I think what threw me originally was the fact that when I tried to login using MySQL Administrator I used my system username (tim) for username and the password I associate with that normally. Logging in as root didn't seem logical at that point.

Now it all seems very simple and actually a very easy set up of LAMP. Can't help thinking that wiki might have been a bit more idiot-proof.

Anyway, thanks for everyone's time.

---

### Post by l.tambiah on 2006-03-13
My apologies for the info i told you above I had to guess without a machine in front of me. Basically you just needed to type "sudo mysql" NOT "sudo mysql -u"

Okay, heres what I did:

I acted as though I forgot my password for mysql. So i removed mysql-server like thus:-

```
**$ sudo apt-get --purge remove mysql-server**
``` 

I then reinstalled the mysql server.

```
**sudo apt-get install mysql-server**
``` 

I then tried to log in with my old password to ensure no user settings are left over from the previous installation. 

```
**mysql -u -p**
``` I then get the error:-ERROR 1045: Access denied for user: 'root@localhost' (Using password: YES)

Now this is what i meant to tell you earlier, first time logging in mysql simply do this:-

```
**sudo mysql**
``` 
and now enter your root password for Ubuntu. This is the password you use to log into Ubuntu.

Now you in mysql you can then set your password:-

```
**mysql> SET PASSWORD = PASSWORD('your password');**
``` 

Now you have set your password we can login. 

```
**$ mysql -u root -p yourPassword**
``` 

In reference to not understanding what root is, it can be confusing. GNU/Linux has a root account which gives you access to all system files. Mysql-server also has a root acount. So in the above context we logged into mysql with the root Ubnutu password and set a root password for the root user in mysql. These are two different root passwords that Ubuntu and mysql use.

May i advise you create a user in your mysql, as you should really avoid working in root.

Hope this helps...

---

