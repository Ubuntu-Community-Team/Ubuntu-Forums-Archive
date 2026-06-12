---
title: "Issues with getting MySQL server to work"
date: 2005-02-14
forum: General Help
---

### Post by voodoostevie on 2005-02-14
Ok I downloaded the MySQL Server package and followed the steps as stated in the Ubuntu Guide:

[list]
[*] $ sudo apt-get install mysql-server
[*]$ sudo /usr/bin/mysqladmin -u root password your_root_user_password
[/list]

Now when I typed in the second part (with my root password mind you) I got:

```
error: 'Access denied for user: 'root@localhost' (Using password: NO)'
```

This came up even after a reboot and MySQL Server appears to be loaded. How can I get this going? I grabbed phpmyadmin to see if I could go in through there and it was giving me:

```
#1045 - Access denied for user: 'root@localhost' (Using password: YES)
```

Suggestions? Help is much needed. I am trying to set my machine up to test things for my website which is using php and MySQL and I need to get into creating the databases to do so.

---

### Post by scoon on 2005-02-14
Hey there, 

Try enabling the root account.  Also go to mysql.com and look over the manual for some more help. 


scoon

---

### Post by voodoostevie on 2005-02-14
I am logged in as root  (sudo -s -H <- performed before installing mysql server package). 

The command was run as per the instructions of the Ubuntu Guide (as stated before).

---

### Post by scoon on 2005-02-14
[QUOTE=voodoostevie]I am logged in as root  (sudo -s -H <- performed before installing mysql server package). 

The command was run as per the instructions of the Ubuntu Guide (as stated before).[/QUOTE]

Hey there, 

sudo is NOT root.  So you may consider trying to enable root and see if that fixes your problem. root is a uid of 0 where your user has a uid of >= 1000

scoon

---

### Post by Darrena on 2005-02-14
[QUOTE=scoon]Hey there, 

sudo is NOT root.  So you may consider trying to enable root and see if that fixes your problem. root is a uid of 0 where your user has a uid of >= 1000

scoon[/QUOTE]

I believe that your system root password is different than the root password to mySQL. 

So try connecting to the mysql shell without a password:
mysql -u root mysql

and then issue the following:
set password = password("yournewpassword");

---

### Post by az on 2005-02-14
"Try enabling the root account"

You do not need do do that.  You should be able to set the root password without there being a root user.

There is no reason do do that in Ubuntu.

---

### Post by scoon on 2005-02-14
[QUOTE=azz]"Try enabling the root account"

You do not need do do that.  You should be able to set the root password without there being a root user.

There is no reason do do that in Ubuntu.[/QUOTE]

Hey there, 

Even tho the root account is "disabled" ?

scoon

---

### Post by valfader on 2005-02-15
There was no password set for root, atleased when I installade it. If your not a mysql wizard, then I would recommend installing myphpadmin, a web based administation tool for mysql. Simply install myphpadmin pkg and apt should install php and apache aswell...

---

### Post by az on 2005-02-15
"You should be able to set the root password without there being a root user."

I meant the root mysql user.

---

### Post by dmeister on 2005-02-19
I'm having the same problem with MySQL which I installed today through apt-get.

I did notice that if I try doing:

[FONT=Courier New]mysql -u root[/FONT]

I get:

[FONT=Courier New]ERROR 1045: Access denied for user: 'root@localhost' (Using password: NO)".[/FONT]

However if I try using the internal IP address, it seems to work:

[FONT=Courier New]mysql -u root@127.0.0.1[/FONT]

So does anyone know the correct process to allow "@localhost" access?

---

### Post by now departed on 2005-02-25
Hi,

I got some trouble myself with posgresql so I turned to MySQL. To my surprise (i am a new linux world part) the basics worked just fine. So here is how I did it.

So like me why don't you use SYNAPTIC to install MySQL ?
Of course everything is done without the user' intervention but it worked fine with me.
The server is launched automatically at boot time. so maube here you can re-boot.
I happen to do what follows the next day.
After, you need to GRANT permissions on the database you wish to create before you can create it (!?). to do this you have to run MySQL with root privileges meaning you type sudo mysql at the command line in a shell. then you use the appropriate GRANT command options (chapter 5.6.2 in the MySQL doc). 
then you quit, re-log to the server as simple user, and then you can create a database and use it.

Hope it helps !

---

### Post by voodoostevie on 2005-02-25
A friend of mine helped me out with this. We uninstalled mysql-server and removed all traces if the settings on the system. We finally got it up. Thanks for the help anyway.

---

### Post by Phosphoros on 2005-03-02
I sholdn't really comment on this since I'm so pissed right now, but I've been trying to get MySQL working for 2 days now.  I guess I'm just to stupid or something to get it to work, I dunno.    ](*,)   I was just trying to install mp3Kult so I could have a nice little database for my MP3's, but after this Mysql nightmare I think I'll pass.
I did try everything here suggested and some of it seemed to work but with the terminal beeping at me like it's on speed and my not having a PhD in Mysql db management I gave up.  :-({|=  

I saw the suggestion from someone to install phpmyadmin, but I have no clue if apache runs at boot or not and I'm so tired of having to google and read through 40 websites and digging through the Ubuntu forums to set a program up.

Sadly, other than MySql, my XMMS nightmare, Mplayer Nightmare, and my a couple other little programs giving me a hard time I **do seriously** love Ubuntu.

Maybe after a couple days I'll give MyFavoriteNightmareSql another try.

Anyone want to make a thorough HOWTO for Ubuntu users on MySql isntallation and the simple task of adding a database?  :)

---

### Post by ensenadaubuntulover on 2005-06-02
[QUOTE=pascal]Hi,

I got some trouble myself with posgresql so I turned to MySQL. To my surprise (i am a new linux world part) the basics worked just fine. So here is how I did it.

So like me why don't you use SYNAPTIC to install MySQL ?
Of course everything is done without the user' intervention but it worked fine with me.
The server is launched automatically at boot time. so maube here you can re-boot.
I happen to do what follows the next day.
After, you need to GRANT permissions on the database you wish to create before you can create it (!?). to do this you have to run MySQL with root privileges meaning you type sudo mysql at the command line in a shell. then you use the appropriate GRANT command options (chapter 5.6.2 in the MySQL doc). 
then you quit, re-log to the server as simple user, and then you can create a database and use it.






this one looks interesting I am going to try it...

If I am not othering you too much.

[COLOR=Red]can I have a GRANT example?
[/COLOR]
[COLOR=Green]you know like a line I can cut and paste and edit?
[/COLOR]

your help will be greatly apreciated!!!

---

### Post by ensenadaubuntulover on 2005-06-02
[QUOTE=Phosphoros]I sholdn't really comment on this since I'm so pissed right now, but I've been trying to get MySQL working for 2 days now.  I guess I'm just to stupid or something to get it to work, I dunno.    ](*,)   I was just trying to install mp3Kult so I could have a nice little database for my MP3's, but after this Mysql nightmare I think I'll pass.
I did try everything here suggested and some of it seemed to work but with the terminal beeping at me like it's on speed and my not having a PhD in Mysql db management I gave up.  :-({|=  

I saw the suggestion from someone to install phpmyadmin, but I have no clue if apache runs at boot or not and I'm so tired of having to google and read through 40 websites and digging through the Ubuntu forums to set a program up.

Sadly, other than MySql, my XMMS nightmare, Mplayer Nightmare, and my a couple other little programs giving me a hard time I **do seriously** love Ubuntu.

Maybe after a couple days I'll give MyFavoriteNightmareSql another try.

Anyone want to make a thorough HOWTO for Ubuntu users on MySql isntallation and the simple task of adding a database?  :)[/QUOTE]
 I really undestand your frustration but with this community I am learning a lot

---

