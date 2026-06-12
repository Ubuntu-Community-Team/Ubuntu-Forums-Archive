---
title: "sudo user broken"
date: 2010-08-01
forum: General Help
---

### Post by noninyo on 2010-08-01
Hi,

I am the only user is on the computer (and there for the sudo user).

I don't know what I did but I can not do anything the require the sudo privilege.

Can someone pleas help me???

10x

---

### Post by Smart Viking on 2010-08-01
you should explain a little deeper, what does the terminal say when you try to use a sudo command? Have you restarted the computer? Make sure no program like Update Manager or Gparted or any other that need root privileges to run are running! :)

---

### Post by noninyo on 2010-08-01
> **Smart Viking said:**
> you should explain a little deeper, what does the terminal say when you try to use a sudo command? Have you restarted the computer? Make sure no program like Update Manager or Gparted or any other that need root privileges to run are running! :)
I restated my computer more then once :)
the only program running is firefox
when I try any comment in the terminal that require a sudo user, after pressing the password I get:
> noninyo is not in the sudoers file.  This incident will be reported.

---

### Post by TNT1 on 2010-08-01
> **noninyo said:**
> I restated my computer more then once :)
the only program running is firefox
when I try any comment in the terminal that require a sudo user, after pressing the password I get:

System/Administration/Users and Groups, make sure your username is added to the sudo group.

---

### Post by noninyo on 2010-08-01
> **TNT1 said:**
> System/Administration/Users and Groups, make sure your username is added to the sudo group.
I can't make any change in the 'users and groups' it require a sudo password.. :(

---

### Post by Smart Viking on 2010-08-01
thats weird, then you are kinda doomed! O.o

Could he use a live CD to change the sudoers text file?

---

### Post by noninyo on 2010-08-01
> **Smart Viking said:**
> thats weird, then you are kinda doomed! O.o

Could he use a live CD to change the sudoers text file?
I don't know what that mean :/

---

### Post by TNT1 on 2010-08-01
> **Smart Viking said:**
> thats weird, then you are kinda doomed! O.o

Could he use a live CD to change the sudoers text file?

A google shows:
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

[http://www.cyberciti.biz/faq/ubuntu-linux-root-password-default-password/](http://www.cyberciti.biz/faq/ubuntu-linux-root-password-default-password/)

This might also be useful:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by noninyo on 2010-08-01
I try using that 
[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

after writing 
>  adduser noninyo admin 
I got this:
> Adding user 'noninyo' to group 'admin'....
Adding user noninyo to group admin
Multiple entries named 'admin' in /etc/group. Please fix this with pwck or grpck.
gpasswd: failed to prepare new /etc/group entry 'admin' 
adduser: '/usr/bin/gpasswd -a noninyo admin' returned error  code 1. exiting

Do you know how can I use the pwck or grpck to fix this problem?

---

### Post by noninyo on 2010-08-02
someone??? plz!!!!
help!!!!!:(

---

### Post by noninyo on 2010-08-02
ok I think I found the problem.... but I don't know how to fix it :/

all the group is my computer is duplicate....



[[IMG]http://ubuntuforums.org/attachment.php?attachmentid=165260&stc=1&thumb=1&d=1280737992[/IMG]]("http://ubuntuforums.org/attachment.php?attachmentid=165260&d=1280737992")
anyone know what can I do???

---

### Post by noninyo on 2010-08-03
ok I fix it!!!

first I edit the group file and sudoers file according to [http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)
and add my self to be root user :)

10x for the help!!!!

---

