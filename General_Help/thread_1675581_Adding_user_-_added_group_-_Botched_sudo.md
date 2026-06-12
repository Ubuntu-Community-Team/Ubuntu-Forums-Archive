---
title: "Adding user - added group - Botched sudo"
date: 2011-01-25
forum: General Help
---

### Post by Jay_E on 2011-01-25
Greetings!

I just installed 10.10  and was getting started.
Sudo worked fine with the user's password.

I added a new user. sudo did not work.
I *assumed* that adding the new user to the admin group would work...
Under the first user (joe), I edited /etc/group - and added the second user name wherever the user 'joe' appeared.

Now, when logged in to either user, Sudo asks me for the password of 'root'.
Yikes.
Rebooting didn't help.

Thanks in advance!!:)

Jay

---

### Post by djeikyb on 2011-01-25
If you have a backup of your /etc folder, restore your old, unedited version of /etc/group. Failing that, undo your changes.

To add a user to a group, use this command:
```
adduser username groupname
```ie```
adduser djeikyb admin
```

---

### Post by hawkmage on 2011-01-25
In general I do not rely on the standard groups for sudo.  I create two groups "sudoall" and "sudoallnp"
```
sudo groupadd sudoall
sudo groupadd sudoallnp
```Then I add these lines to the sudoers file using visudo.  
```
%sudoall ALL=(ALL) ALL
%sudoallnp ALL=NOPASSWD: ALL
```Then I use "usermod" to add the group to the user.  

Here is a transcript of the command (visudo step is not suown):
```
hawkmage@ubuntu:~$ sudo groupadd sudoall
hawkmage@ubuntu:~$ sudo groupadd sudoallnp
hawkmage@ubuntu:~$ id -Gn jdoe
users accounting games 
hawkmage@ubuntu:~$ sudo usermod -a -G sudoall jdoe
hawkmage@ubuntu:~$ id -Gn jdoe
users accounting games sudoall
hawkmage@ubuntu:~$ sudo su - jdoe
jdoe@ubuntu:~$ sudo -l
[sudo] password for jdoe:
User jdoe may run the following commands on this host:
    (ALL) ALL
jdoe@ubuntu:~$ exit
logout
hawkmage@ubuntu:~$ 
```

---

### Post by Jay_E on 2011-01-26
AH-Hah
I used ":", Not the required ","  as a separator.

Thank you for your help and interesting alternatives!!!!

Jay

---

