---
title: "Undeletable file"
date: 2010-12-11
forum: General Help
---

### Post by halen666 on 2010-12-11
HI guys,
I install Apache/MySQL/PHP on ubuntu because I am trying to install webcollab; however, I need to modify a filke called "php.ini" It is located in /etc/php5/apache2/

The problem I have is that I cannot modify the file no matter what I do. I have even used the root account (su -) with no luck. I get this error
when I try to edit it with nano:  [Error writing php.ini: Read-only file system]

I have tried to change the attributes with no luck
Here is the output of ls -l:
-rw-r--r-- 1 root root 67459 ............

Here is the output from lsattr
-----------------e- php.ini

I tried to used chattr -e on it with no luck. The damn file is indestructible. Like I said, I used the root account, but even with that account I cannot modify it, change attributes, etc. Please I need help to increate the upload file size for files.

Thank you

---

### Post by Old_Grey_Wolf on 2010-12-11
Unless you have enabled the root account on Ubuntu, the su - command does not work. Try using sudo instead.

---

### Post by halen666 on 2010-12-11
I have tried both

sudo user_name .........
su -
then I get the root prompt, I have even used whoami and get root back

---

### Post by Dave_L on 2010-12-11
Use this command to edit the file:

sudo nano /etc/php5/apache2/php.ini

That will prompt for your password.

---

### Post by lisati on 2010-12-11
Try this:
```
sudo nano /etc/php5/apache2/php.ini
```

---

### Post by halen666 on 2010-12-11
I think I didn't explain myself correctly. I know how to use root to modify files; likewise, I know how to use sudo accounts (in this case my own user account with sudo at the beginning) to do stuff. However, even when I do that I cannot edit the file.

Example:

sudo nano /etc/php5/apache2/php.ini

then I edit the file and make the changes I need to do......

then when I save the file I get
[Error writing php.ini: Read-only file system]

which tells me there is a attribut problem. 
I typed sudo USER_NAME chmod 666 php.ini
but I get an error saying I cannot change the attributes because it is read-only, then
I try
su -
user_name~# whoiam
root
user_name~# chmod 666 php.ini

but then I get the same error.
Then I try to change the attribues with root, but it fails to do so. I get the same errors.
Here are the attributes for the file:

Here is the output of ls -l:
-rw-r--r-- 1 root root 67459 ............

Here is the output from lsattr
-----------------e- php.ini


I hope this helps better to understand what my problem is.

Thank you

---

### Post by Dave_L on 2010-12-11
Is Apache running? Are there unusual messages in its error log?

Can you create or modify other files in that directory?

Is that directory mounted separately?

The command "mount", with no arguments, lists all the mounts.

I googled for that error message, and the only article I found said there might be a file system problem, and suggested running "fsck" on the partition.

---

