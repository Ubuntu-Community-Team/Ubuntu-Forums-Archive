---
title: "Cant add new user!"
date: 2010-09-16
forum: General Help
---

### Post by samer19 on 2010-09-16
Hello,

When I go to user settings and try to add a new user, I get this error message:
"This configuration could not be saved" You are not allowed to modify..

Even though i'm logged in as the admin.  I'm running Ubuntu, the latest version.

As of now, my account is labeled as "custom". I try to make it admin, yet it reverts back to custom.

---

### Post by linuxonbute on 2010-09-16
> **samer19 said:**
> Hello,

When I go to user settings and try to add a new user, I get this error message:
"This configuration could not be saved" You are not allowed to modify..

Even though i'm logged in as the admin.  I'm running Ubuntu, the latest version.

As of now, my account is labeled as "custom". I try to make it admin, yet it reverts back to custom.

When you say you are logged in as the admin do you mean a user you created?

The first user you create at install time should be a member of the sudoers group by default.

This user should be able to do what you want.

---

### Post by samer19 on 2010-09-16
I'm logged as in the user created during the installation process.

---

### Post by CharlesA on 2010-09-16
You should be able to create a user. You may have to "unlock" it first tho.

---

### Post by samer19 on 2010-09-16
how can i unlock it?

---

### Post by SlugSlug on 2010-09-16
sudo adduser 'username'

---

### Post by CharlesA on 2010-09-16
Hrm, I just tried it and it wouldn't do anything.

How are you connected?

You could try adding the user thru the ***useradd***

---

### Post by samer19 on 2010-09-16
> **SlugSlug said:**
> sudo adduser 'username'

boss@boss-laptop:~$ sudo adduser feline
Adding user `feline' ...
Adding new group `feline' (1002) ...
groupadd: cannot lock /etc/group; try again later.
adduser: `/usr/sbin/groupadd -g 1002 feline' returned error code 10. Exiting.
boss@boss-laptop:~$

---

### Post by SlugSlug on 2010-09-16
> **samer19 said:**
> boss@boss-laptop:~$ sudo adduser feline
Adding user `feline' ...
Adding new group `feline' (1002) ...
groupadd: cannot lock /etc/group; try again later.
adduser: `/usr/sbin/groupadd -g 1002 feline' returned error code 10. Exiting.
boss@boss-laptop:~$


try close your add user program and try again -- if not reboot and try again -- if not you may need to remove two files from /ect..


 /etc/group.lock and /etc/gshadow.lock.

---

### Post by samer19 on 2010-09-16
> **SlugSlug said:**
> try close your add user program and try again -- if not reboot and try again -- if not you may need to remove two files from /ect..


 /etc/group.lock and /etc/gshadow.lock.

boss@boss-laptop:~$ rm /etc/group.lock
rm: remove write-protected regular empty file `/etc/group.lock'? y
rm: cannot remove `/etc/group.lock': Permission denied
boss@boss-laptop:~$

---

### Post by WorMzy on 2010-09-16
You'll need to use "sudo rm" to remove those files, they're owned by root, not you.

---

### Post by SlugSlug on 2010-09-16
> **WorMzy said:**
> You'll need to use "sudo rm" to remove those files, they're owned by root, not you.


^^ what he said

---

### Post by samer19 on 2010-09-16
Ok It worked, thanks guys.

The question is, what were those files and where they important? (the shadow lock files)

---

### Post by SlugSlug on 2010-09-16
Linux locks files to stop two things editing the same file (for instance you may get this error if you open synaptc & try use apt-get)

your safe to remove them if you know why they are locked & why you need to remove them ;)

---

### Post by soop on 2011-01-04
FYI ... I just noticed this same error can occur if trying to create a user with a "." in the id ... eg B.Smith 

If you drop to the terminal and do:

 "adduser B.Smith" --force-badname  

It will allow you to do it ...


Ubuntu version 10.10


I don't know why the user creation screen would say you can use these characters and then disallow it with an ambiguous error message in the gui

---

