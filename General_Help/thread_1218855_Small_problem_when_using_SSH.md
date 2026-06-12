---
title: "Small problem when using SSH"
date: 2009-07-21
forum: General Help
---

### Post by codingfreak on 2009-07-21
Hi

I have a strange problem when I do SSH to a FEDORA9 based Linux Server.

```
$ ls -al /home/
total 68
drwxr-xr-x 16 root    root         4096 2009-07-21 09:30 .
drwxr-xr-x 22 root    root         4096 2009-07-21 08:36 ..
lrwxrwxrwx  1 root    root           25 2009-06-19 10:52 adah -> /media/disk-1/home/adah
lrwxrwxrwx  1 root    root           24 2009-06-19 10:45 ajsin -> /media/disk-1/home/ajsin
lrwxrwxrwx  1 root    root           25 2009-06-19 10:53 akhtam -> /media/disk-1/home/akhtam
```As you see from the above information that symbolic links were created for accounts adah, akhtam and so on.

When I login using "**adah**" username in TELNET I am automatically directed to my home directory at location "**/media/disk-1/home/adah**".

But when I use SSH to login using the same username I get the following message

```
Could not chdir to home directory /home/adahaj: Permission denied
```How can I rectify above problem ???

---

### Post by bacil on 2009-07-21
Your simlink is owned by root should be owned by user. ssh i sensitive to this

---

### Post by codingfreak on 2009-07-21
> **bacil said:**
> Your simlink is owned by root should be owned by user. ssh i sensitive to this
I have used "**chown**" command and changed for the user "**adah**"
```

$ ls -al /home/
total 68
drwxr-xr-x 16 root    root         4096 2009-07-21 09:30 .
drwxr-xr-x 22 root    root         4096 2009-07-21 08:36 ..
lrwxrwxrwx  1 adah  users          25 2009-06-19 10:52 adah -> /media/disk-1/home/adah
```But still I get the "permission denied error" if I login using SSH for the user "**adah**".

---

### Post by nikhilk on 2009-07-21
> **codingfreak said:**
> I have used "**chown**" command and changed for the user "**adah**"
```

$ ls -al /home/
total 68
drwxr-xr-x 16 root    root         4096 2009-07-21 09:30 .
drwxr-xr-x 22 root    root         4096 2009-07-21 08:36 ..
lrwxrwxrwx  1 adah  users          25 2009-06-19 10:52 adah -> /media/disk-1/home/adah
```But still I get the "permission denied error" if I login using SSH for the user "**adah**".

I think the entry in /etc/passwd is causing this problem. You can modify the home directory of an user via the useradd command.
Check```
man useradd
``` for details.

---

### Post by codingfreak on 2009-07-21
> **nikhilk said:**
> I think the entry in /etc/passwd is causing this problem. You can modify the home directory of an user via the useradd command.
Check```
man useradd
``` for details.

Are you sure about the problem is in **/etc/passwd** as the user "**adah**" is able to access his home directory once logged in. "adah" is getting permission denied error only at the starting when he login using SSH instead of telnet.

---

### Post by nikhilk on 2009-07-21
What is the home directory of user "adah" according to "/etc/passwd"?
But hold that, instead of using simlinks can't you directly change home directory using useradd or somesuch?

---

### Post by codingfreak on 2009-07-22
> **nikhilk said:**
> What is the home directory of user "adah" according to "/etc/passwd"?

It is /home/adah

I think useradd can be useful to create a new user but not change the existing user specifications.

---

### Post by nikhilk on 2009-07-22
> **codingfreak said:**
> It is /home/adah

I think useradd can be useful to create a new user but not change the existing user specifications.

How about usermod then? From usermod man page
"-d, --home homedir This option specifies the new home directory of the user."

---

### Post by codingfreak on 2009-07-22
> **nikhilk said:**
> How about usermod then? From usermod man page
"-d, --home homedir This option specifies the new home directory of the user."

I tried out even modifying /etc/passwd file with usermod but still I am getting the same error. Even though home directory in /etc/passwd files is "**/media/disk-1/home/adah**".

```
$ ssh adah@localhost
Warning: Permanently added 'localhost' (RSA) to the list of known hosts.
adah@localhost's password: 
Last login: Wed Jul 22 15:05:38 2009 from 

WELCOME TO LINUX SERVER ....

Could not chdir to home directory /media/disk-1/home/adah: Permission denied
[adah@localhost /]$ pwd
/
[adah@localhost /]$ 
```

---

### Post by nikhilk on 2009-07-22
You have posted previoulsy that the permissions for the soflink are correct and also you can telnet OK. So just to confirm, are the permissions on the target, "/media/disk-1/home/adah", also OK?

---

### Post by codingfreak on 2009-07-22
> **nikhilk said:**
> You have posted previoulsy that the permissions for the soflink are correct and also you can telnet OK. So just to confirm, are the permissions on the target, "/media/disk-1/home/adah", also OK?

At "/media/disk-1/home/"

```
drwx------ 32 adah   users 4096 2009-07-22 11:20 adah
```

---

### Post by nikhilk on 2009-07-22
Hmm, I am not sure if this will work but try ```
chmod 0755 /media/disk-1/home/adah
``` and see if the problem is resolved.

---

