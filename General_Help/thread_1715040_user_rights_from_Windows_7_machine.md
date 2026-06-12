---
title: "user rights from Windows 7 machine?"
date: 2011-03-26
forum: General Help
---

### Post by jimstolz76 on 2011-03-26
Hey all,

I have an Ubuntu 10.10 headless box that I map a drive array to on a Win7 machine.  Everything works perfectly except Windows never remembers the login credentials no matter what settings or startup scripts I try.

Isn't there a way I can create user accounts on the Ubuntu machine FOR the Windows 7 users?

Example:
Windows 7 Machine - 
Computer Name: Feather-MAC
Workgroup: WORKGROUP
Users: Jim, Feather


Forgive me if I'm using the wrong terminology...

---

### Post by Frogs Hair on 2011-03-26
I little more information may help . User accounts for each operating system would have to be setup from that operating system as far as I know.

---

### Post by jimstolz76 on 2011-03-26
Well I changed it so the login and password on the Ubuntu machine was the same as the Windows 7 machine, but I still get prompted for a user name and account when I try to connect to the mapped drive.  That's why I was thinking that maybe I needed to create a user account in Ubuntu that somehow included the Win7 machine name.  

(...but I'm just grasping at straws...)

What other info do you need?

---

### Post by Morbius1 on 2011-03-26
I'm getting a little lost here. 

If Windows is passing a username:jim and passwd:jimpassword then there has to be a username:jim on the Ubuntu machine and the passwd has to be exactly the same as the local login password for jim on Ubuntu.

This behavior is new to 10.10 because of one package that is installed by default: **[COLOR=Black]libpam-smbpass[/COLOR]**. That package will override whatever you set with smbpasswd to the local Ubuntu login password for that user.
[COLOR=Blue]EDIT[/COLOR]: *I should have noted that that override will happen at reboot not during that session.*

Before, you could set the samba password to be different from the local login password. If this describes what your are experiencing then the best thing to do is:
```
sudo apt-get remove libpam-smbpass
```

---

### Post by jimstolz76 on 2011-03-26
So in other words I should just set up identical usernames and passwords on both the Win7 and Ubuntu machines, correct?

I actually just realized that my laptop (also with the same credentials) DOES connect to the mapped drive just fine, so maybe I'm overcomplicating this and just need to figure out what my other Windows machine is doing (shocker...)

Thanks guys.

---

### Post by Morbius1 on 2011-03-26
>          So in other words I should just set up identical usernames and passwords on both the Win7 and Ubuntu machines, correct?I would argue just the opposite. Remove libpam-smbpass and Samba returns to the way it's worked for decades. I makes no sense to me to have identical user names AND passwords on all machines in the network.

---

