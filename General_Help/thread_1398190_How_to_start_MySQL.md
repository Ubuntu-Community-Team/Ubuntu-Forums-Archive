---
title: "How to start MySQL"
date: 2010-02-04
forum: General Help
---

### Post by AmirM on 2010-02-04
I installed MySQL server with terminal
```
  sudo apt-get install mysql-server
```
what I have to do in the next step?
I installed "MySQL Administrator" with Add/Remove,but how I have to connect?

---

### Post by howefield on 2010-02-04
Open a terminal (Applications > Accessories > Terminal) and type

```
mysql-administrator
```

---

### Post by AmirM on 2010-02-04
```
amir@Desktop:~$ mysql-administrator
bash: mysql-administrator: command not found
amir@Desktop:~$ 

```

:(

---

### Post by konqueror7 on 2010-02-04
```
mysqladmin
```

also, you can start/stop/restart mysql via terminal,
```
sudo service mysql start
sudo service mysql stop
sudo service mysql restart
```

EDIT: mine was the CLI version, @howefield has the GUI version...

---

### Post by dekadance on 2010-02-04
do as konqueror7 says or ...go to Main Menu (ALT+F1) > programming-> MySQL Administrator...The shortcut should be there in the menu if it has installed properly :)
you need to read further documentation on how to use it found here:
[http://dev.mysql.com/doc/administrator/en/index.html](http://dev.mysql.com/doc/administrator/en/index.html)

take care:)

---

### Post by howefield on 2010-02-04
Just checked on my server

```
mysql-admin
```

---

### Post by AmirM on 2010-02-04
> **konqueror7 said:**
> ```
mysqladmin
```also, you can start/stop/restart mysql via terminal,
```
sudo service mysql start
sudo service mysql stop
sudo service mysql restart
```EDIT: mine was the CLI version, @howefield has the GUI version...
I done this.i donno what to do then!

> **dekadance said:**
> do as konqueror7 says or ...go to Main Menu (ALT+F1) > programming-> MySQL Administrator...The shortcut should be there in the menu if it has installed properly :)
you need to read further documentation on how to use it found here:
[http://dev.mysql.com/doc/administrator/en/index.html](http://dev.mysql.com/doc/administrator/en/index.html)

take care:)

its OK to go there.the shortcut is there and when I click that it opens a window asking for connections,hostname,etc.
I donno what informations to put there.

> **howefield said:**
> Just checked on my server

```
mysql-admin
```
on mine:
```
amir@Desktop:~$ mysql -admin
mysql: unknown option '-a'

```

---

### Post by howefield on 2010-02-04
> **AmirM said:**
> 
```
amir@Desktop:~$ mysql -admin
mysql: unknown option '-a'

```

There is no space in the command. It is

```
mysql-admin
```

---

### Post by AmirM on 2010-02-04
> **howefield said:**
> There is no space in the command. It is

```
mysql-admin
```

my mistake!:)
and what's the information to fill?(I know it depends on the user ans systems but need a help)

---

### Post by jenaniston on 2010-02-04
> **AmirM said:**
> I done this.i donno what to do then!


now just

```
# service mysql status
```tells if is running . . . 
or if it is stopped . . .

---

### Post by konqueror7 on 2010-02-04
lol,,,you have executed every command? that was only an example on managing MySQL server via CLI,,,anyway, default username would be root, port 3306, server localhost, and password depends on what you've entered during the installation,,,

---

### Post by AmirM on 2010-02-04
> **konqueror7 said:**
> lol,,,you have executed every command? that was only an example on managing MySQL server via CLI,,,anyway, default username would be root, port 3306, server localhost, and password depends on what you've entered during the installation,,,

sure I didn't executed ALL of command!! what do you think of me??!!:)
thank you and others for help,but before your last response I did it this way and everything worked:
1.in the terminal:
```
sudo mysql-admin
```2.hostname:localhost
3.NO usernames
4.password: password that I was choosed.

---

### Post by AmirM on 2010-02-04
:(:(:(
where are the things?
where to create databases?to execute SQL commands?

---

### Post by konqueror7 on 2010-02-04
> **AmirM said:**
> sure I didn't executed ALL of command!! what do you think of me??!!:)
thank you and others for help,but before your last response I did it this way and everything worked:
1.in the terminal:
```
sudo mysql-admin
```2.hostname:localhost
3.NO usernames
4.password: password that I was choosed.

i just thougth so,,,:D

---

### Post by howefield on 2010-02-04
> **AmirM said:**
> but need a help)

Then I guess you find a tutorial ;)

[http://dev.mysql.com/tech-resources/articles/mysql_intro.html](http://dev.mysql.com/tech-resources/articles/mysql_intro.html)
[http://www.roseindia.net/mysql/mysql-administrator.shtml](http://www.roseindia.net/mysql/mysql-administrator.shtml)


The main configuration tool for dealing with sql databases I use is webmin, I find it easier to work with.

---

### Post by AmirM on 2010-02-04
> **Our export control systems have identified your request for access as non-compliant to the United States export control laws.**
  A required IP lookup revealed that your IP address is originating from an embargoed country.
 Therefore, we are unable to grant you access from your current IP location
see where I live????](*,)](*,):-x:(

---

### Post by jenaniston on 2010-02-04
> **AmirM said:**
> see where I live????](*,)](*,):-x:(
Honestly ? . . . 
Your country does not allow you to look on the internet for even a mysql tutorial . . . that could be a predicament.

---

### Post by AmirM on 2010-02-04
> **jenaniston said:**
> Honestly ? . . . 
Your country does not allow you to look on the internet for even a mysql tutorial . . . that could be a predicament.

my country allows me but MySQL staff and laws of U.S dont!!
its the matter of sanctions...(I live in Iran)

---

### Post by jenaniston on 2010-02-04
> **AmirM said:**
>  . . . laws of U.S dont!!
its the matter of sanctions...

Maybe there were just some bad experiences with mysql databases in the past that led to that restriction. 
It may take some time now.

---

### Post by AmirM on 2010-02-04
> **jenaniston said:**
> Maybe there were just some bad experiences with mysql databases in the past that led to that restriction. 
It may take some time now.
no,the matter is some stupid ******** done a kidnapping **30 YEARS AGO** and NOW I'm not allowed to do a lot of thing.(I cant access google codes and google chrome,cant download from sourceforge,etc just because of sanctions)

enough with politics! lets help me create some databases with MySQL server...

p.s:dont worry,I use that sites with tunnels and proxies!

---

