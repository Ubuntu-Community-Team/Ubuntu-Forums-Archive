---
title: "Lamp Help!"
date: 2006-04-26
forum: General Help
---

### Post by chocolatetoothpaste on 2006-04-26
I really need some help here.  I feel kind of dumb having this problem.  I have been trying to set up a web development environment on my machine, but I have had little success.  I have the linux bible 2k6 edition, and it steps you through a basic LAMP setup.  I got it working for the most part, except for the virtual hosts.  That is a must because I maintain several sites.  Well, when that didn't work, I went to wiki.ubuntu.com/Apache and tried to follow the instructions there.  I got to the point where you setup mysql and it kept giving me an authentication error.  Now, I don't claim to be a wiz at the mysql command line.  I just need help setting up my environment.  I have searched through numerous articles on the net, but can't get anywhere.
For mysql I type in
```

 mysql -u root mysql

```
and I get
```

ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)

```
Currently I have installed Apache2, php4 and mysql 4.1(I think).  If anyone can please help, I would greatly appreciate it.  I am not looking for anything more than this, just apache, php and mysql.  Thanks.

---

### Post by adamkane on 2006-04-26
> 
Breezy

Enable Universe repository:
[http://easylinux.info/wiki/Ubuntu#How_to_add_extra_repositories]("http://easylinux.info/wiki/Ubuntu#How_to_add_extra_repositories")

Install LAMP:
 ```

sudo apt-get install apache2 php4 mysql-client mysql-server libapache2-mod-php4 libapache2-mod-auth-mysql php4-mysql phpmyadmin

``` 
 
> 
Dapper

Enable Universe repository:
[http://easylinux.info/wiki/Ubuntu_dapper#How_to_add_extra_repositories]("http://easylinux.info/wiki/Ubuntu_dapper#How_to_add_extra_repositories")

Install LAMP:
  ```

sudo apt-get install apache2 php5 mysql-client mysql-server libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql phpmyadmin

``` 
   
> 
Breezy or Dapper

 Open this address in your browser:
 [http://localhost/phpmyadmin]("http://localhost/phpmyadmin")
 
 Log in:
 name: root
 pass: [blank]
 

You now have easy access to your databases and users.

If the install doesn't work, you'll need to re-install Ubuntu, then re-install LAMP according to these directions.

---

### Post by ZylGadis on 2006-04-27
That's the most ridiculous piece of advice I've heard in a long time. Resintall LAMP? Reinstall Ubuntu? Dude, the need for advices like yours is what this community is trying to get away from.

To the original poster: I'm not sure what mysql's default root password is. You should be able to find it easily in mysql's documentation for the version you use. Then the correct command is (having assured that mysqld has started and listens on localhost:3306):

mysql -uroot -ppassword database

Assuming the password is blank, you'd need:

mysql -uroot -p database

Alternatively you can skip the "database" part, but when you enter the mysql command line client, the first thing you should do is "use mydb", or "create database mydb" and then "use mydb".
Hope that helps.

---

### Post by adamkane on 2006-04-27
It's the best advice for new users, and is the quickest way to get them up and running with LAMP and phpmyadmin.

There aren't enough LAMP experts trolling the forums to help all the new LAMP users with messed-up installs.

If the new user starts with a standard LAMP install, it is **much** easier to help them when they have problems, if they start with a standard install.

There are tons of new user LAMP questions, and I'm trying to keep it as simple and easy as possible for the new user.

It is **much** easier to use phpmyadmin to change users/passwords, and is recommended for new users.

If it turns out the new user ends up with a standard installation that doesn't work, it's easiest to just start from the beginning. Troubleshooting takes forever, and usually doesn't resolve to a solution.

---

### Post by ZylGadis on 2006-04-27
Your first post sounds exactly like what Microsoft technical support would have said. I don't think any person in their right mind would appreciate generic troubleshooting advice, present in the manual, that does nothing to alleviate their current problems.

"Hey, my volume is a little high... how can I lower it?"
"Reinstall Windows."

Ever heard of that?

---

### Post by chocolatetoothpaste on 2006-04-27
Well, I hate phpMyAdmin.  I use the command line for very basic stuff, but I am clueless as far as the permissions and users junk goes.  I interact very little with the database.  I let my php scripts do the work.
  I am definitely not looking to reinstall ubuntu.  I got in the bad habit of doing that with windows, and I am not reinstalling until dapper.  After that, I won't reinstall, just distro-upgrade.
  [ZylGadis]("http://ubuntuforums.org/member.php?u=56653"), I will try what you said, hopefully that will take care of the problem.

---

