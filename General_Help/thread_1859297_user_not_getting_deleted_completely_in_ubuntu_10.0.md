---
title: "user not getting deleted completely in ubuntu 10.04 LTS"
date: 2011-10-13
forum: General Help
---

### Post by pmx on 2011-10-13
hi,

I deleted the an additional user (which I created) with the following command:

```
deluser --remove-all-files linuxworld
```but the linuxworld is still appearing in the System -> Administration -> Users and Groups

Also, while logging in to the ubuntu 10.04 (LTS) desktop, that user is listed. So how do I remove that?

After that, here is the complete history and error details:

The user to be deleted ('linuxworld') is appearing in the /etc/passwd

```
cat /etc/passwd 
```in the output, the last line is as follows:

```
linuxworld:x:1001:1001:linuxworld,,,,:/home/linuxworld:/bin/bash
```The error I am getting is this one. And the user to be deleted is 'linuxworld'

```
myfamily@myfamily-desktop:~$ userdel -f linuxworld 
 userdel: cannot lock /etc/passwd; try again later.
 myfamily@myfamily-desktop:~$ sudo userdel -f linuxworld 
  [sudo] password for myfamily: 
 userdel: cannot lock /etc/gshadow; try again later.
``````
myfamily@myfamily-desktop:~$ ls /etc/*.lock
/etc/gshadow.lock
myfamily@myfamily-desktop:~$ 

myfamily@myfamily-desktop:~$ sudo cat /etc/gshadow.lock 
myfamily@myfamily-desktop:~$ 

```gshadow.lock file has no contents to be displayed!!

I don't know what to do now? Don't know what these files are and doing?  Simply tried to delete the user from Users and Groups but again not  successfull!

---

