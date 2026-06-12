---
title: "How is super user in authentication prompt determined"
date: 2010-05-03
forum: General Help
---

### Post by indiecom on 2010-05-03
How is the super user determined for the dialog box that pops up when trying to perform administrative tasks, "An application is attempting to perform an action that requires  privileges. Authentication as the super user is required to perform this  action."? Does it always ask for the password of the default user created during the OS install, or should it prompt for the current user's password if that person is an administrator?

I use likewise-open for windows domain authentication, so I typically log in as a windows user that likewise-open has added to the list of users on this system. I have given this user sudo access and added the user to all the same groups as the default user, yet whenever I perform an administrative task in gnome I am prompted for the password of the default user. Is this normal? It seems like the behavior would be to ask for the current user's password if that user is an administrator, and if so what determines that the current user is an administrator?

---

### Post by darolu on 2010-05-03
You need to add the user to the sudoers list, you can do this with "visudo":
```
$ sudo visudo
```
Although adding the user to the Admin or Sudo group should do the trick.

---

### Post by rnerwein on 2010-05-03
hi indiecom
first - i hope it's not to late.
second - there are some possibilties to use the /etc/sudoers file to make the life easier ( this file is very sensitive and just a little mistake
can made your system ( nearly ) unusable ).
the other way is to open the root account and then login as root ( but then you are ( nearly ) back to windows.
i think you will check it out by your self the way how to do it.
have much fun 
ciao

---

### Post by indiecom on 2010-05-03
> **darolu said:**
> You need to add the user to the sudoers list, you can do this with "visudo":
```
$ sudo visudo
```Although adding the user to the Admin or Sudo group should do the trick.

Thanks for the quick response! Actually this user is already in the sudoers file, which is what puzzles me. As my current windows user:

```
winuser@desktop:~$ sudo whoami
root
winuser@desktop:~$ gksudo whoami
root
```Here's the changes I made in sudoers, I added:

```
User_Alias      ADMIN = %admin, %WINDOMAIN\\domain^admins
ADMIN ALL=(ALL) ALL
```User "winuser" is a member of group "WINDOMAIN\\domain^admins". Even though I clearly have sudo to root access, the administrative tasks  dialog asks me for the default user's password.

Let's call the default user "localuser". So when I try to do something administrative as winuser, I get the authentication dialog asking me for "[...]Authentication as the super user is required to perform this action. Password for localuser:". Any ideas why that might upset the graphical environment's handling of administrative authentication?

---

### Post by indiecom on 2010-05-03
Oh man, found the issue. I added my user to all the same groups as the default user *except one*, and that one was admins. (edit: When I added myself to the admins group it started working as expected). So it looks like graphical administrative access is determined specifically by membership in the group admins, not just sudo root access. Oh well, good to know.

Thanks to everyone who replied so quickly!

---

