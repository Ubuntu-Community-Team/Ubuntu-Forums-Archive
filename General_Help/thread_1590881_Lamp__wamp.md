---
title: "Lamp / wamp"
date: 2010-10-08
forum: General Help
---

### Post by Blue Summer on 2010-10-08
We've been using Wamp at college to learn some php, making a login script and a register script which writes to a database on phpmyadmin or something like that, I was told to use LAMP in linux, so I followed a thread on the forums to install LAMP and now I can't find the program anywere, anyone know where it installs by default?

---

### Post by searchfgold6789 on 2010-10-08
There are some programs, such as TIemu, that do not appear in the menu, and you must run the program from the terminal.
Have you tried just typing ```
lamp
``` into the terminal?

---

### Post by screaminfakah on 2010-10-08
[http://www.lamphowto.com/](http://www.lamphowto.com/)

---

### Post by Blue Summer on 2010-10-08
> **screaminfakah said:**
> [http://www.lamphowto.com/](http://www.lamphowto.com/)


wow that's ridiculously complicated, I think I might just dual boot or give up with it tbh

---

### Post by WorMzy on 2010-10-08
LAMP and WAMP aren't programs, they're a collection of programs. The L and W stand for Linux and Windows respectively. The A stands for Apache2, the M stands for MySQL5, and the P stands for PHP5.

If you have installed LAMP on your Ubuntu machine through
```
sudo tasksel install lamp-server
```
or something similar, then you should now have everything set up and working. Ubuntu does it all automagically for you. All you need to do now is put your PHP files in /var/www and point your browser to [http://localhost]("http://localhost") or [http://127.0.0.1]("http://127.0.0.1").

You may want to chown the /var/www directory so that you can add/edit files in it without having to be root. To do so, run:

```
sudo chown -R $USER:$USER /var/www
```

---

### Post by Blue Summer on 2010-10-08
Thank you for that mate, just wondering how I access phpadmin thing to set up a quick database?

---

### Post by WorMzy on 2010-10-08
That doesn't come with a standard LAMP installation, you need to install it separately with ```
sudo apt-get install phpmyadmin
```

You need to set up mysql before you can use it though, so run:

```
sudo mysql_secure_installation
```

and follow the prompts.

Afterwards, you'll be able to log into phpmyadmin at [http://localhost/phpmyadmin/]("http://localhost/phpmyadmin/").

---

### Post by Blue Summer on 2010-10-08
Turns out I've already installed it, so how do I access it?

sorry one more quick question, how can I make a shortcut to the var/www folder on my desktop?

---

### Post by WorMzy on 2010-10-08
> **Blue Summer said:**
> Turns out I've already installed it, so how do I access it?
> **WorMzy]Afterwards, you'll be able to log into phpmyadmin at [http://localhost/phpmyadmin/]("http://localhost/phpmyadmin/"). [/QUOTE]


[QUOTE=Blue Summer said:**
> sorry one more quick question, how can I make a shortcut to the var/www folder on my desktop?

Right-click on your desktop and choose "Create Launcher", in the dialogue box change the Type to "Location", and enter "/var/www" in the Location box (don't add the quotes, but the slashes are important). Then click OK.


EDIT: If you're getting a 404 error when trying to view PHPMyAdmin, then run the following:
```
gksu gedit /etc/apache2/apache2.conf
```
In this file add the following to the bottom of the file:
```
Include /etc/phpmyadmin/apache.conf
```

EDIT EDIT: You'll probably need to restart apache after changing that file, so run:
```
sudo service apache restart
``` or ```
sudo /etc/init.d/apache restart
``` depending on which version of Ubuntu you're using. Try the service one first.

---

### Post by SeijiSensei on 2010-10-08
While you might want to start with phpmyadmin, if you intend to pursue this type of work at school or thereafter, I'd recommend you get comfortable with the command-line mysql client and the SQL query language itself.

sudo apt-get install mysql-client

Once you have a database created, you can access it by running the command 

mysql -u username -p password database_name

replacing username and password with the ones that own database_name.

You'll get a prompt and can then type in queries manually.  Start with a few simple SELECT queries, learn how to sort the results, how to filter the query with a WHERE clause, and so forth.  You'll understand much better what's happening behind the scenes in phpmyadmin.

---

### Post by Blue Summer on 2010-10-08
Yeah I'm getting that "oops This link appears to be broken message" in chrome, i've added the line in apache config but the 2 restarting apache codes don't work for me

---

### Post by Blue Summer on 2010-10-09
sorry to bump =)

---

### Post by WorMzy on 2010-10-09
Sorry, those commands should have had "apache2" in them, not "apache"

```
sudo service apache2 restart
```

```
sudo /etc/init.d/apache2 restart
```

---

