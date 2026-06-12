---
title: "Too Many Open Files Error @$%&amp;*!!!"
date: 2010-09-29
forum: General Help
---

### Post by WithoutAClue on 2010-09-29
A recent hard drive crash lost the only "official" copy of Windows 7 my computer came with - a recovery partition.
After buying another hard drive, I decided to simply install Ubuntu 10.04 as the OS rather than fight to get another copy of Windows 7, or worse, buy one.

Anyhow, my laptop is only, and exclusively, used to store multiple documents, journals, research papers, forms, e-books, etc. in various formats that are accessed through various library/archive software.  Some only contain a few hundred such files while other libraries contain several thousands.

When attempting to open a library containing more than the *magic 1024 files*, I get the dreaded **"too many open files" error** and cannot open that library.

I have searched this topic extensively for days now and have tried ***ulimit -n 10240***,  added ***fs.file-max = 10240*** to*** /etc/sysctl.conf***, have added **** - nofile 10240*** (*along with every conceivable combination of hard/soft, users, etc.*) , to** */etc/security/limit.d***, added ***session required pam_limits.so*** to** */etc/pam.d/common_session***, etc., etc., and like everyone else who has had this problem found that none of these did a **@#&*$ bit of good!!!!**

I can run these libraries through ***nautilus*** as the*** root user*** after using the command ***ulimit -n 10240*** but other people need access to this laptop and I do not intend to give everyone that access nor have to log on as the root user every time to simply use this computer for its intended purpose....

***IS THERE A SOLUTION????  SHOULD I JUST GO BACK TO MS???***

---

### Post by WithoutAClue on 2010-09-29
From what I have found on Google this is a common problem with Linux...  No one has a solution?  Does anyone know where the original 1024 open file restriction is hidden (kernel? boot? bin? etc...)?

---

### Post by P4man on 2010-09-30
First of all, which filesystem are you using? Im using ext4 and apparently I have no limit. 

```
bob@bob-desktop:~$ ulimit
unlimited
```

Do you have the same?

I just tried it and copied a bunch of empty files and I now have over 3000 files in a folder.

---

### Post by WithoutAClue on 2010-09-30
To see the "open file" restrictions, type ***ulimit -n ***in terminal, it will come back with ***1024***.

---

### Post by dino99 on 2010-09-30
i have this 1024 ulimit too on maverick i386

do you really need more than this huge amount ? Maybe check the partition(s) free space and the swap. I never had such problem on my end.

The solution for custom user settings is to use "profile" for your needs and set the rights accordingly, then create an other profile ( or more) for average user(s)

[https://help.ubuntu.com/community/EnvironmentVariables](https://help.ubuntu.com/community/EnvironmentVariables)

---

### Post by P4man on 2010-09-30
> **WithoutAClue said:**
> To see the "open file" restrictions, type ***ulimit -n ***in terminal, it will come back with ***1024***.

Yes, you are right. 1024 here is well.
OTOH, it doesnt seem to prevent me from having thousands of files in a folder?

[IMG]http://a.yfrog.com/img94/2738/77988705.png[/IMG]

5000+ and all visible? Those are just empty files though, no idea if that changes anything.

---

### Post by gzarkadas on 2010-09-30
First, please specify the kind of libraries that give you this error: filename extension, application that is used to open them, number of files inside, type (ie extension) of files, etc. 

Then please post your /etc/security/limits.conf here, as well as the output of `ulimit -a' in your affected user account.

Since you can open as root your libraries, it is not an inability of the system to open them; it is just that the configuration didn't get right.

---

