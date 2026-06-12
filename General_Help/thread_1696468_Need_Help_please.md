---
title: "Need Help please"
date: 2011-02-27
forum: General Help
---

### Post by ArrikOK on 2011-02-27
I seem to have lost root privileges when trying to get my cam to work on tinychat. I though you could put your user into multiple groups but it took me out of the sudo group. The problem is it asks me for the Root Password but I didn't set one when I installed it. I need the root password to do anything now... I just need to switch to the sudo group so I can figure out how to put my user in the different groups... I need my user in the following groups:

Admin
Adm
Video
Sudo

But in order to do that I need the root password which I do not know. I need help in the matter if someone is kind enough to help.

---

### Post by marshmallow1304 on 2011-02-27
[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

After you're in recovery mode, use Case 1 to add yourself back into the admin group.

---

### Post by grahammechanical on 2011-02-27
If you do not know the root password then you should understand that no one here knows the root password either.

Are you the person that installed Ubuntu? Do you remember setting a user name and a password during the installation process? Then you do know the root password!

Ubuntu works differently to some other Linux distributions. In Ubuntu we do not work as root. We use a program called sudo. When we try to do something that requires root or administration privileges then we are asked to authenticate or put in a password. We put in our password (we are the administrator). We gain access to do what we want. Then when we are finished the sudo program removes our access as administrator automatically and we continue working as a normal user. And our machine is secure.

If we are using a terminal then when we issue a command that needs root or administration privileges then we type sudo in front of the command. We are asked for our password. Again our root privileges last only for that command.

Go to System>Administration>Users and Groups. Select your user name and see what your Account type is. Click on Advanced Settings and see what privileges you have. Of course, if you are not the administrator then you will not have the password. Will you?

Regards.

---

### Post by ArrikOK on 2011-02-27
> **marshmallow1304 said:**
> [http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

After you're in recovery mode, use Case 1 to add yourself back into the admin group.

And what about adding my user to the Sudo group? It's not broken that I know...

---

