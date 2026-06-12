---
title: "Cannot create any other user"
date: 2012-05-27
forum: General Help
---

### Post by amandat on 2012-05-27
Hi,

I have had trouble signing in using the Guest login, and so thought I would just make a new User for my friend who is using my laptop. 

I have tried to add a user multiple times, and have got the attached screen whenever I try.

I have also tried multiple times to log in using the Guest login. When I have tried, all that appears is a black screen with white writing (I cannot press 'print screen' quickly enough to catch it). It then goes back to the Log In screen. 

This was a problem in both 11.04 and 12.04. 

What can I do? I have a friend borrowing my laptop, and he is relying on borrowing it...

---

### Post by kc1di on 2012-05-27
well if you don't mind using the command line in a terminal here's how to do it.
[http://www.cyberciti.biz/faq/howto-linux-add-user-use-adduser-command/]("http://www.cyberciti.biz/faq/howto-linux-add-user-use-adduser-command/")

---

### Post by amandat on 2012-05-28
Hi Dave, 

Thank you very much :)

However, terminal came back with:

amanda@amanda-Satellite-L40:~$ useradd <Gareth>
bash: syntax error near unexpected token `newline'
amanda@amanda-Satellite-L40:~$ sudo useradd <Gareth>
bash: syntax error near unexpected token `newline'
amanda@amanda-Satellite-L40:~$ sudo useradd -m Gareth -p x
[sudo] password for amanda: 
useradd: cannot lock /etc/passwd; try again later.
amanda@amanda-Satellite-L40:~$ sudo useradd -m Gareth -p x
useradd: cannot lock /etc/passwd; try again later.

Is this usual etc??

---

### Post by derklempner on 2012-05-28
My suggestion would be to forget the **useradd** command and try using the **adduser** command instead.

---

### Post by amandat on 2012-05-28
Thank you again :)

However, I tried this, and got this:

amanda@amanda-Satellite-L40:~$ sudo adduser Gareth
[sudo] password for amanda: 
adduser: Please enter a username matching the regular expression configured
via the NAME_REGEX[_SYSTEM] configuration variable.  Use the `--force-badname'
option to relax this check or reconfigure NAME_REGEX.
amanda@amanda-Satellite-L40:~$ sudo adduser gareth
Adding user `gareth' ...
Adding new group `gareth' (1001) ...
groupadd: cannot lock /etc/group; try again later.
adduser: `/usr/sbin/groupadd -g 1001 gareth' returned error code 10. Exiting.

---

### Post by philinux on 2012-05-28
> **amandat said:**
> Thank you again :)

However, I tried this, and got this:

amanda@amanda-Satellite-L40:~$ sudo adduser Gareth
[sudo] password for amanda: 
adduser: Please enter a username matching the regular expression configured
via the NAME_REGEX[_SYSTEM] configuration variable.  Use the `--force-badname'
option to relax this check or reconfigure NAME_REGEX.
amanda@amanda-Satellite-L40:~$ sudo adduser gareth
Adding user `gareth' ...
Adding new group `gareth' (1001) ...
groupadd: cannot lock /etc/group; try again later.
adduser: `/usr/sbin/groupadd -g 1001 gareth' returned error code 10. Exiting.

See this and post 9 onwards. 

 [http://ubuntuforums.org/showthread.php?t=1575865](http://ubuntuforums.org/showthread.php?t=1575865)

---

### Post by derklempner on 2012-05-28
> **philinux said:**
> See this and post 9 onwards. [http://ubuntuforums.org/showthread.php?t=1575865](http://ubuntuforums.org/showthread.php?t=1575865)
I was about to suggest the same thing.  See if any of the following files exist:

[B]/etc/group.lock
/etc/gshadow.lock
/etc/shadow.lock
/etc/passwd.lock[/B]

If you find them, delete them and then try creating a new user.

---

### Post by amandat on 2012-05-28
Thank you very much! 

It is now working fine, and I am able to create other users without hassle.

---

### Post by kc1di on 2012-05-29
Glad it's fixed for you :)
please take moment and mark the this thread as solved.
Thank you,
Dave

---

