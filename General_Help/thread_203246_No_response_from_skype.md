---
title: "No response from skype"
date: 2006-06-24
forum: General Help
---

### Post by seshomaru samma on 2006-06-24
Hi
I installed Skype on Dapper using the .deb file from their website. I don't use it often and I remeber it worked before but lately I had to make some calls and Skype wouldn't run at all . I click on the Icon - nothing happens, when I ran it from the terminal I get :
```
sesho@ubuntu:~$ skype
*** glibc detected *** free(): invalid pointer: 0x08a23130 ***
Aborted
```
what's an invalid pointer?

---

### Post by Evoreth on 2006-06-25
You're using SCIM, huh? SCIM and Skype doesn't seem to like each other. :(

---

### Post by seshomaru samma on 2006-06-25
[QUOTE=Evoreth]You're using SCIM, huh? SCIM and Skype doesn't seem to like each other. :([/QUOTE]

I do...
But I need SCIM 
Is there a way around it?

---

### Post by shaahrazade on 2006-09-16
It is possible to install skype packages from the japanese repositories, which goes well with scim and japanese input.
Just add the following to the sources.list:

```
deb http://archive.ubuntulinux.jp/ubuntu-ja dapper/
deb http://archive.ubuntulinux.jp/ubuntu-ja dapper-ja/
```

and reinstall skype.

---

