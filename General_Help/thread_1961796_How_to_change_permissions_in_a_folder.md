---
title: "How to change permissions in a folder?"
date: 2012-04-19
forum: General Help
---

### Post by piek on 2012-04-19
[newby] - Just setup ubuntu and currently learning PHP. I tried to save a text editor file as a test in the var/www folder, however I got the following error:

"You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again."

When I right clicked in the folder and went to properties, it said, "you are not the owner, so you cannot change these permissions." I am the admin in this linux account, so I'm not quite sure what to do. Subsequently, all the options in the "permissions" tab are all un-clickable. 

Thanks in advance for any help.

---

### Post by Vaphell on 2012-04-19
your account is able to elevate its privileges with sudo/gksudo, but it doesn't mean that your account is allowed to modify stuff outside home dir by default, no questions asked

if you want to run editor in admin mode press ctrl+alt+t to run terminal and type
```
gksu gedit
```
type your user password and this gedit instance should be able to modify contents of directories other than your home.

---

### Post by mccartyj on 2012-04-19
Using chmod...

This page has a nice little calculator:
[What CHMOD?]("http://www.classical-webdesigns.co.uk/resources/whatchmod.html")

Wikipedia gives a more in depth explanation that's pretty helpful if you want to understand the various codes.

Typically it looks like this:
```
sudo chmod ??? file.txt
```

For the ??? you can use the octal codes the the first link gives you. The digits are broken into OWNER GROUP PUBLIC and range from 0 to 7. READ = 4, WRITE = 2, and EXECUTE = 1. To get the final permission you add up the numbers for each category.

For example: I want a file only I can read, write, and execute and the public can read.

For OWNER that is 4 (read) + 2 (write) + 1 (execute) = 7

For GROUP no permissions = 0

For PUBLIC 4 (read) = 4

So the command becomes:
```
sudo chmod 704 file.txt
```

If you wanted to do that for the whole directory, just make it recursive:
```
sudo chmod -R 704 /var/www/myDir 
```

You could also use chown to change the owner or chgrp to change the group of the file/directory...

---

### Post by HiImTye on 2012-04-20
you can also use chmod in this way:
who:[INDENT]u=user (owner)
g=group
o=other
a=all
[/INDENT]action:[INDENT]+=add
-=subtract
==set
[/INDENT]permission:[INDENT]r=read
w=write
x=execute
X=special execute (skip files without existing execute permissions)
s=setuid/setgid
t=sticky
[/INDENT]for instance, set execute for files with at least one execute bit set plus read/write for all files in /path/to/set for the owner and his group and set execute for files with at least one execute bit set plus read for others:
```
chmod -R ug=rwX,o=rX /path/to/set/
```

---

### Post by piek on 2012-04-20
When entering this code, I get the following output:

chmod: invalid mode: 'ug=rwX,'

> **HiImTye said:**
> you can also use chmod in this way:
who:[INDENT]u=user (owner)
g=group
o=other
a=all
[/INDENT]action:[INDENT]+=add
-=subtract
==set
[/INDENT]permission:[INDENT]r=read
w=write
x=execute
X=special execute (skip files without existing execute permissions)
s=setuid/setgid
t=sticky
[/INDENT]for instance, set execute for files with at least one execute bit set plus read/write for all files in /path/to/set for the owner and his group and set execute for files with at least one execute bit set plus read for others:
```
chmod -R ug=rwX,o=rX /path/to/set/
```

---

### Post by piek on 2012-04-20
After entering the code, I can't see any uploaded files at all now. It says:

**Forbidden**

 You don't have permission to access / on this server.


 
Apache/2.2.22 (Ubuntu) Server at localhost Port 80

> **mccartyj said:**
> Using chmod...

This page has a nice little calculator:
[What CHMOD?]("http://www.classical-webdesigns.co.uk/resources/whatchmod.html")

Wikipedia gives a more in depth explanation that's pretty helpful if you want to understand the various codes.

Typically it looks like this:
```
sudo chmod ??? file.txt
```For the ??? you can use the octal codes the the first link gives you. The digits are broken into OWNER GROUP PUBLIC and range from 0 to 7. READ = 4, WRITE = 2, and EXECUTE = 1. To get the final permission you add up the numbers for each category.

For example: I want a file only I can read, write, and execute and the public can read.

For OWNER that is 4 (read) + 2 (write) + 1 (execute) = 7

For GROUP no permissions = 0

For PUBLIC 4 (read) = 4

So the command becomes:
```
sudo chmod 704 file.txt
```If you wanted to do that for the whole directory, just make it recursive:
```
sudo chmod -R 704 /var/www/myDir 
```You could also use chown to change the owner or chgrp to change the group of the file/directory...

---

### Post by piek on 2012-04-20
Now when I type into the terminal, "chmod -R 704 /var/www" it said the following:

chmod: changing permissions of `/var/www': Operation not permitted
chmod: cannot access `/var/www/index.html': Permission denied
chmod: cannot access `/var/www/testing.html': Permission denied
chmod: cannot access `/var/www/testing.html~': Permission denied

---

### Post by raja.genupula on 2012-04-20
> **piek said:**
> Now when I type into the terminal, "chmod -R 704 /var/www" it said the following:

chmod: changing permissions of `/var/www': Operation not permitted
chmod: cannot access `/var/www/index.html': Permission denied
chmod: cannot access `/var/www/testing.html': Permission denied
chmod: cannot access `/var/www/testing.html~': Permission denied

You should be root to do this because you are trying to deal with the filesystem

---

### Post by Vaphell on 2012-04-20
you don't need privilege escalation to change permissions only when you work with your own files. /var/www is not yours, so you need to wield the admin hammer - sudo

besides chmodding to 7 will make everything executable, which is wrong. Directories need x bit, but ordinary non-executable files don't so dirs should be odd and files even.

if you need finer control use find command
```
find /var/www -type d -exec chmod ... "{}" \;
find /var/www -type f -exec chmod ... "{}" \;
```
with appropriate permissions for each category.

---

### Post by piek on 2012-04-20
I apologize, but this is all new to me. Before, when I typed in localhost on my browser, it said, "It works!" which means apache was working. Now, I get an error after I typed in the -R 704 code in the terminal. I'm following the "Beginning PHP 5.3" book, and on the second chapter where I'm testing to see if everything works. Can anyone tell me how to get the text editor "gedit" to save with permission in the directory, var/www and how to have apache working again to display content which is uploaded to that directory? Again, I apologize if my request is silly, I am just starting to learn the ropes. Really appreciate all your help. Thanks.

> **Vaphell said:**
> you don't need privilege escalation to change permissions only when you work with your own files. /var/www is not yours, so you need to wield the admin hammer - sudo

besides chmodding to 7 will make everything executable, which is wrong. Directories need x bit, but ordinary non-executable files don't so dirs should be odd and files even.

---

### Post by Vaphell on 2012-04-20
well, it's pretty much mandatory to understand the implications of chmod and chown commands before playing with them. In some places in system directories one wrong set of permissions = full reinstallation.

can you post the output of ls -l /var/www ?

---

### Post by piek on 2012-04-20
> **Vaphell said:**
> well, it's pretty much mandatory to understand the implications of chmod and chown commands before playing with them. In some places in system directories one wrong set of permissions = full reinstallation.

can you post the output of ls -l /var/www ?

ls: cannot access /var/www/index.html: Permission denied
ls: cannot access /var/www/testing.html: Permission denied
ls: cannot access /var/www/testing.html~: Permission denied
total 0
-????????? ? ? ? ?            ? index.html
-????????? ? ? ? ?            ? testing.html
-????????? ? ? ? ?            ? testing.html~

---

### Post by piek on 2012-04-20
Can someone add me via Skype. Real-time help is probably better ;-)

Skype handle = phpdetox

Thanks!

---

### Post by Vaphell on 2012-04-20
this is why directories require +x - to allow running commands in them :)

i think this should restore original settings
sudo chmod 755 /var/www
sudo chmod 644 /var/www/*

now
ls -l /var/www

it will tell you owner and group
imho you should add your account to the group (if it's not root) and set
permissions 775/664 (middle digit is group)

to achieve that
```
sudo usermod -a -G group_name your_name
```

---

### Post by mccartyj on 2012-04-20
> **piek said:**
> Now when I type into the terminal, "chmod -R 704 /var/www" it said the following:

chmod: changing permissions of `/var/www': Operation not permitted
chmod: cannot access `/var/www/index.html': Permission denied
chmod: cannot access `/var/www/testing.html': Permission denied
chmod: cannot access `/var/www/testing.html~': Permission denied

Sorry... I didn't mean for you to use "704", I was just making an example of how chmod works. It looks like you got some more accurate advice to split up the directories and files...

IIRC, all of the files for your site need to be publicly readable at a minimum.

My /var/www is 755 for the directory and 644 for the files like Vaphell stated. I don't use PHP, but my website scripts are all 755 (rwx for me rx for others).

---

### Post by mccartyj on 2012-04-20
Looks like this guy had a similar problem. The second answer down (from Tom) should cover what you need. Its a combination of all of the advice given so far on this thread...

[User permissions for /var/www]("http://serverfault.com/questions/6895/whats-the-best-way-of-handling-permissions-for-apache2s-user-www-data-in-var#6899")

You can skip the "userb" stuff (unless you are trying to do this for 2 users as well).

Good luck!

---

### Post by piek on 2012-04-20
yay! After typing in:
sudo chmod 755 /var/www
sudo chmod 644 /var/www/*

now
ls -l /var/www

The output is:
-rw-r--r-- 1 root root 177 Apr 18 23:58 index.html
-rw-r--r-- 1 root root 101 Apr 20 11:52 testing.html
-rw-r--r-- 1 root root 101 Apr 20 11:13 testing.html~


Thanks for your help guys! :-)

> **Vaphell said:**
> this is why directories require +x - to allow running commands in them :)

i think this should restore original settings
sudo chmod 755 /var/www
sudo chmod 644 /var/www/*

now
ls -l /var/www

it will tell you owner and group
imho you should add your account to the group (if it's not root) and set
permissions 775/664 (middle digit is group)

to achieve that
```
sudo usermod -a -G group_name your_name
```

---

### Post by piek on 2012-04-27
Hi guys, 

I'm still having a permissions problem. When trying to save in the text editor, it has the following error:
"You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again."

When inputting "ls -l /var/www" In the terminal, it outputs:

"-rw-r--r-- 1 root root 177 Apr 18 23:58 index.html
-rw-r--r-- 1 root root 105 Apr 20 14:50 testing.html
-rw-r--r-- 1 root root 104 Apr 20 14:48 testing.html~
-rw-r--r-- 1 root root  22 Apr 20 14:54 testing.php
"
Please advise.

---

### Post by mccartyj on 2012-05-01
So now those files belong to root but are readable by everyone. Only root has write access.

```
 sudo chown username filename 
``` 
will fix that. Then in the future create files without using the sudo command and they should automatically be in your possession.

You could also chown the whole /var/www directory by adding a -R to the command (before the username).

---

