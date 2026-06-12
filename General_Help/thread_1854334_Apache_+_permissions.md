---
title: "Apache + permissions"
date: 2011-10-04
forum: General Help
---

### Post by 7Sasha on 2011-10-04
Hi. 
I cant manage setting the permissions properly.
I've got a local apache running.
I'm trying to use the following Vhost file (default)

[PHP]<VirtualHost *:80>
	ServerName test
	DocumentRoot /home/sasha/www/test/
	<Directory /home/sasha/www/test/>
		Options +Indexes +FollowSymLinks
		AllowOverride All
	</Directory>
</VirtualHost>[/PHP]

I get the error

```
[Tue Oct 04 12:33:52 2011] [crit] [client 127.0.0.1] (13)Permission denied: /home/sasha/.htaccess pcfg_openfile: unable to check htaccess file, ensure it is readable

```

It's looking for htaccess in a directory above the document root
and obviously it does not have the permission to access it.

What is the right way to set the permissions?
Apache running as www-data group, www-data user.

Thanks in advance.

---

### Post by prodigy_ on 2011-10-04
I'm more familiar with nginx, but IMHO it shouldn't even try reading anything above Document Root. Something's wrong elsewhere in your Apache config I guess.

---

### Post by binary00mind on 2011-10-04
> **7Sasha said:**
> Hi. 
I cant manage setting the permissions properly.
I've got a local apache running.
I'm trying to use the following Vhost file (default)

[PHP]<VirtualHost *:80>
	ServerName test
	DocumentRoot /home/sasha/www/test/
	<Directory /home/sasha/www/test/>
		Options +Indexes +FollowSymLinks
		AllowOverride All
	</Directory>
</VirtualHost>[/PHP]

I get the error

```
[Tue Oct 04 12:33:52 2011] [crit] [client 127.0.0.1] (13)Permission denied: /home/sasha/.htaccess pcfg_openfile: unable to check htaccess file, ensure it is readable

```

It's looking for htaccess in a directory above the document root
and obviously it does not have the permission to access it.

What is the right way to set the permissions?
Apache running as www-data group, www-data user.

Thanks in advance.You have setup your test apache configuration in your /home directory and it seems that root owns it. To edit virtual host you must go to /etc directory and the rest to /var/www directory. 
take a look at this official documentation link[[COLOR="Blue"] Official instructions of setting up apache2 for Ubuntu 10.04[/COLOR]](https://help.ubuntu.com/10.04/serverguide/C/httpd.html) 
If you want to install LAMP and for example wordpress you must change permission to the database. The best thing is to follow the instructions/documentation.  

Note#1 I never tested I just installed. 
Note#2 As for changing permissions you navigate to the directory, open the terminal and change the needed permissions to the database. 
Do not use this command ```
chown -R www-data:www-data 
```
Read documentation of whatever you are trying to install. 
You will find what permissions must be changed. 
Try to read this [[COLOR="Blue"]File Permissions-Numerical corresponding to Read/Write/Execute and sticky [/COLOR]](https://help.ubuntu.com/community/FilePermissions)

---

### Post by prodigy_ on 2011-10-04
> **binary00mind said:**
> You have setup your test apache configuration in your /home directory and it seems that root owns it.
**/home** defaults to 755 and so does any user folder in it. And while **/var/www** is indeed the default location, other folders should work as well.

The OP's problem is that Apache is looking for a file somewhere where it isn't even supposed to look.

---

### Post by 7Sasha on 2011-10-04
> **prodigy_ said:**
>  Something's wrong elsewhere in your Apache config I guess.
That's possible, though all the configs are the default ones
[my apache2.conf]("http://pastebin.com/E6RVGebV")

> You have setup your test apache configuration in your /home directory and it seems that root owns it.
How do I set it up in /home/sasha/www, rather then /home ?

In either case, the only location i'd like to give www-data access to is the www directory **only**.

---

### Post by binary00mind on 2011-10-04
In my previous post I wrote that you set it up your Apache in /home directory and you took this literally. 

My point was that it should be in the /var/www directory
versus your setup /home/sasha/www 
  
In my case, my current LAMP/wordpress setup is
/var/www 
I don't know your partitions layout and how big they are. 
How much room you have to make all workable. 
I have 4 partition 
/Root 50 GB and 40 GB full
/home 220 GB and 210 GB full 
/swap
/var 35 GB and 12 GB full. 
I install things according to documentations and commonly accepted practice. 
With the exception of little things, like proven ppa's

If you install Apache in your /home/you/www folder then you have to put/home/sasha/www folder to your group (sasha) and set permission that /www data folder can write and read in that folder. 
plus the various Apache *.conf/sites/ports should be in the /etc directory. and all the symlinks pointing there

I don't know what version of Ubuntu you are having but from what I have seen in the latest beta version, is that it does not offer GUI settings of group(s) and users membership. 
(there is a package "members" which could be little helpful-basically it is an obsolete package-but without GUI that leaves you with the terminal and setting up all this using command line)  

Also not everything is set up to 755 permissions in the /home directory...I do save my marks in my /home/marks folder before applying changes in the Synaptic Package Manager and that folder "marks" is owned by the root..I can only read it. 

The symlinks must be setup correctly pointing to /etc/apache2 directories plus variables must be set up too..and all the other symlinks should be pointing to data directory which commonly is located in /var/www/ (in your case /home/sasha/www)

All errors you will find in this directory /usr/share/apache2/error 

Personally I always read documentation and stay away from Internet Blogs offering quick fixes. 

Read again the link that I posted before with the Apache2 documentation.

---

### Post by 7Sasha on 2011-10-04
Thanks for your reply, but no part of it was helpful.
Apache is installed into /etc/apache2, all it's files (conf, sites, ports, mods) are placed there.

I just want the virtual host to take files from a different directory. 
For some reason - apache is trying to look for htaccess in a directory above the DocumentRoot, which should not happen. It fails obviously because it does have no permissions to access that directory. 

Since this is the default installation of apache (apt-get install apache2)
i guess that i've messed something up with user permissions / group permissions,
since it had been working properly in previous installations with the very same steps.


I might be wrong and it has nothing to do with permissions.

---

### Post by 7Sasha on 2011-10-05
When the virtual hosts lead to /var/www everything works properly.
This are the permissions set:

```
sasha@subi:/var/www$ ls -al

drwxr-xr-x  2 root root 4096 2011-10-04 11:14 .
drwxr-xr-x 16 root root 4096 2011-10-04 11:14 ..
-rw-r--r--  1 root root  177 2011-10-04 11:14 index.html

sasha@subi:/home/sasha/test$ ls -al

drwxr-xr-x  2 sasha sasha 4096 2011-10-05 07:28 .
drwx------ 52 sasha root  4096 2011-10-05 07:28 ..
sasha@subi:~/test$ 

```

Notice that /var/www is owned by root and still apache's proccess has access to it.
How is that possible ?

---

### Post by 7Sasha on 2011-10-05
I've just noticed that my home directory is drwx------ 
while i guess it should be 755 instead. That would give apache read access to it
and solve my problems. Am I right?

---

### Post by Doug S on 2011-10-05
> **7Sasha said:**
> I've just noticed that my home directory is drwx------ 
while i guess it should be 755 instead. That would give apache read access to it
and solve my problems. Am I right?Yes.

---

