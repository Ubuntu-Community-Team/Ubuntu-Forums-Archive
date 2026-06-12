---
title: "Setting Permissions, please help?"
date: 2012-06-22
forum: General Help
---

### Post by MiD-AwE on 2012-06-22
I have an installation of lampp in /opt/ I recently installed Joomla! 2.5 and I need to change all the permissions to allow me to run and install for development. No one has access to my system but me alone. Please I'm sure that this is a simple GNU/Linux Ubuntu 12.04 question but I have not learned many terminal commands but I understand them when I see them. Thank you for your help. :confused:

---

### Post by LinXNut on 2012-06-22
In the terminal, navigate to the **folder** that joomla is in, but don't go into the folder. When you find the folder, type:

```
sudo chmod 777 name of folder
```

The chmod changes the file. The first 7 sets the owner of the file to be able to read write and execute. The second 7 allows another group to r/w/e, and the third 7 allows others to r/w/e. I have never done this before, but I think this should help. (:

---

### Post by bab1 on 2012-06-22
> **MiD-AwE said:**
> I have an installation of lampp in /opt/ I recently installed Joomla! 2.5 and I need to change all the permissions to allow me to run and install for development. No one has access to my system but me alone. Please I'm sure that this is a simple GNU/Linux Ubuntu 12.04 question but I have not learned many terminal commands but I understand them when I see them. Thank you for your help. :confused:

This may not be as simple as you think, then again it might be.  Linux folder permissions use the eXecute bit to allow traversal or descending into that folder.  The default permissions have changed with 12.04.  You are running Ubuntu; right?  What version are you running?

The default owner:group  of /opt is root:root.  Are you running as root when you are using Joomla?  We shouldn't do that.  It is fixable.

---

### Post by MiD-AwE on 2012-06-22
Yes, I'm running 12.04. I always login and I do not believe anything is root. I'm running a simple lampp web-server so that I can develop my Joomla website before I upload it.

---

### Post by bab1 on 2012-06-22
> **MiD-AwE said:**
> Yes, I'm running 12.04. I always login and I do not believe anything is root. I'm running a simple lampp web-server so that I can develop my Joomla website before I upload it.

From the terminal command line (CLI) post the output of this```
ls -ld /opt
``` 

Post the putput between the [code] blocks using the # icon at the top of the editor.

---

### Post by MiD-AwE on 2012-06-22
```
drwxr-xr-x 4 root root 4096 May 25 07:29 /opt

```

---

### Post by bab1 on 2012-06-22
> **MiD-AwE said:**
> ```
drwxr-xr-x 4 root root 4096 May 25 07:29 /opt

```

This looks unmodified (good!).  Post the output of this ```
ls -l /opt
```

This should show what directories and files are in /opt that are 1 level down.  If you have directory **[COLOR="DarkRed"]joomla[/COLOR]** or some such, please provide that out put with something like this```
ls -l /opt/[COLOR="DarkRed"]joomla[/COLOR]
```

At what level are you having trouble with permissions?

---

### Post by MiD-AwE on 2012-06-23
```
ls -l /opt/lampp/htdocs/mid-awe.com
total 108
drwxrwxrwx 11 chuck  chuck    4096 Jun 22 13:19 administrator
drwxrwxrwx  2 chuck  chuck    4096 Jun 22 11:28 cache
drwxrwxrwx  2 chuck  chuck    4096 Jun 22 11:28 cli
drwxrwxrwx 17 chuck  chuck    4096 Jun 22 11:28 components
-rw-rw-rw-  1 chuck  chuck    2105 Jun 22 13:26 configuration.php
-rw-rw-rw-  1 chuck  chuck    2116 Jun 22 13:22 configuration.php~
-rw-r--r--  1 nobody nogroup  3118 Jun 19 07:09 htaccess.txt
drwxrwxrwx  5 chuck  chuck    4096 Jun 22 14:32 images
drwxrwxrwx  2 chuck  chuck    4096 Jun 22 11:28 includes
-rw-rw-rw-  1 chuck  chuck    1319 Jun 22 13:15 index.php
drwxrwxrwx  4 chuck  chuck    4096 Jun 22 11:28 language
drwxrwxrwx  9 chuck  chuck    4096 Jun 22 11:28 libraries
-rw-rw-rw-  1 chuck  chuck   17816 Jun 22 13:15 LICENSE.txt
drwxrwxrwx  2 chuck  chuck    4096 Jun 22 11:28 logs
drwxrwxrwx 16 chuck  chuck    4096 Jun 22 11:28 media
drwxrwxrwx 32 chuck  chuck    4096 Jun 22 13:18 modules
drwxrwxrwx 13 chuck  chuck    4096 Jun 22 11:28 plugins
-rw-rw-rw-  1 chuck  chuck    4244 Jun 22 13:15 README.txt
-rw-rw-rw-  1 chuck  chuck     865 Apr  2 13:13 robots.txt
drwxrwxrwx  7 chuck  chuck    4096 Jun 22 11:28 templates
drwxrwxrwx  3 chuck  chuck    4096 Jun 22 17:37 tmp
-rw-rw-rw-  1 chuck  chuck    1715 Jun 22 13:15 web.config.txt

```
I tried a chown and then chmod to give me all permissions but I cannot tell if it worked. This list looks odd to me because everything should have the same properties AFAIK.

---

### Post by bab1 on 2012-06-23
> **MiD-AwE said:**
> ```
ls -l /opt/lampp/htdocs/mid-awe.com
total 108
[COLOR="Blue"]drwxrwxrwx 11 chuck  chuck    4096 Jun 22 13:19 administrator
drwxrwxrwx  2 chuck  chuck    4096 Jun 22 11:28 cache
drwxrwxrwx  2 chuck  chuck    4096 Jun 22 11:28 cli
drwxrwxrwx 17 chuck  chuck    4096 Jun 22 11:28 components[/COLOR]
[COLOR="Green"]-rw-rw-rw-  1 chuck  chuck    2105 Jun 22 13:26 configuration.php
-rw-rw-rw-  1 chuck  chuck    2116 Jun 22 13:22 configuration.php~
-rw-r--r--  1 nobody nogroup  3118 Jun 19 07:09 htaccess.txt[/COLOR]
drwxrwxrwx  5 chuck  chuck    4096 Jun 22 14:32 images
drwxrwxrwx  2 chuck  chuck    4096 Jun 22 11:28 includes
-rw-rw-rw-  1 chuck  chuck    1319 Jun 22 13:15 index.php
drwxrwxrwx  4 chuck  chuck    4096 Jun 22 11:28 language
drwxrwxrwx  9 chuck  chuck    4096 Jun 22 11:28 libraries
-rw-rw-rw-  1 chuck  chuck   17816 Jun 22 13:15 LICENSE.txt
drwxrwxrwx  2 chuck  chuck    4096 Jun 22 11:28 logs
drwxrwxrwx 16 chuck  chuck    4096 Jun 22 11:28 media
drwxrwxrwx 32 chuck  chuck    4096 Jun 22 13:18 modules
drwxrwxrwx 13 chuck  chuck    4096 Jun 22 11:28 plugins
-rw-rw-rw-  1 chuck  chuck    4244 Jun 22 13:15 README.txt
-rw-rw-rw-  1 chuck  chuck     865 Apr  2 13:13 robots.txt
drwxrwxrwx  7 chuck  chuck    4096 Jun 22 11:28 templates
drwxrwxrwx  3 chuck  chuck    4096 Jun 22 17:37 tmp
-rw-rw-rw-  1 chuck  chuck    1715 Jun 22 13:15 web.config.txt

```
I tried a chown and then chmod to give me all permissions but I cannot tell if it worked. This list looks odd to me because everything should have the same properties AFAIK.

I  see what you have done and that is okay as far as running a machine that is used only by you.  All the directories are rwx by anyone logged into this host and that is why the system user ***nobody*** was allowed to create a file with the group ***nogroup***.  If this works for you then fine.  You might  have to change some permissions once in a while.

If you want to set the permissions to a more secure setting then we will have to change a few things.  I assume you are *chuck* and your primary group is *chuck*.

If you are going to have multiple users working on this project you would want to have a common group such as www-dev so that all web developers could create files and the group would stay the same.  At that point you don't need to worry about who is the creator (owner) as the group has rwx on the directory and the files would be rw for the group and the creater  (owner).  

Bear in mind that with Linux file permissions the owner has no special permissions other than rwx, just as the group.  In you case here everyone has rwx.  They can read, write, delete and execute scripts.

Also any new file with have rw for user and group and r for others.  Just as the file the user nobody created```
-rw-r--r--  1 nobody nogroup  3118 Jun 19 07:09 htaccess.txt
```

Is everything that you need to change permissions and ownership in this directory (mid-awe.com) and below?

---

### Post by MiD-AwE on 2012-06-23
Thank you :) I'll do that. Thanks again. :)

---

