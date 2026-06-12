---
title: "User creation help"
date: 2009-10-22
forum: General Help
---

### Post by craighton on 2009-10-22
I have a VPS that runs Ubuntu server,I have a root account that was setup for me and it has all the basic commands "apt-get" "wget" etc.

I am trying to create a user and I can create a user but when that user signs in and tries to do "apt-get" or "wget" it gives a bash error. Is there something that I can do to get it to work?

---

### Post by OpenGuard on 2009-10-22
[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

---

### Post by redmk2 on 2009-10-22
> **craighton said:**
> I have a VPS that runs Ubuntu server,I have a root account that was setup for me and it has all the basic commands "apt-get" "wget" etc.

Are you saying you can use su to become root?  Or, do you mean that your account can use sudo?> 

I am trying to create a user and I can create a user but when that user signs in and tries to do "apt-get" or "wget" it gives a bash error. Is there something that I can do to get it to work?I'm curious, what is the error, exactly?

Are you sure you set the user up correctly?  Does the user have a valid shell?  The command wget does not require sudo root privileges and should work without having to edit sudoers. OpenGuard is correct if  you want to use sudo to perform apt-get with this user.

---

