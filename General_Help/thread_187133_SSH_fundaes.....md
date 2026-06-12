---
title: "SSH fundaes...."
date: 2006-06-02
forum: General Help
---

### Post by the_witch_king on 2006-06-02
HI , i want to know if there is anyway to do the following.

1. To know who has been using ssh to connect to my system
2. While they connect, can i make a message appear saying X is trying to connect to your system, allow him Yes or No.
3.Can i display a custon welcome message when a person connects to my computer
4.Can i control what he does, like can i allow him only to view stuff and not create directories and files of is own

---

### Post by mbeierl on 2006-06-05
[QUOTE=the_witch_king]
1. To know who has been using ssh to connect to my system[/QUOTE]
Well, there are a few ways:
[LIST=1]
[*]make sure everyone has their own username/password
[*]if you are in an environment where dns works and can be used (ie: home or internal corporate network), you can 'guess' who is connecting based off point of origin.
[/LIST]

[QUOTE=the_witch_king]
2. While they connect, can i make a message appear saying X is trying to connect to your system, allow him Yes or No.
3.Can i display a custon welcome message when a person connects to my computer[/QUOTE]
For 3, yes.  If you make a file in the user's home directory under the .ssh directory, called rc, you can place custom commands in it.  For example if the user is "guest", you would make the file:

/home/guest/.ssh/rc

and can put the following in it:

cat /etc/motd.$USER

Then in the file /etc/motd.guest you can put whatever custom message you want.

As for the ask yes/no, while you could put that in this same file, the user can control-c out of it and still gain access.  I'm not sure why you would want to interactively allow/deny logins.  If they have the password, they should be allowed to get in.  I think it would become annoying to you to constantly be having to answer the login question, and the user would be forced to wait until you can acknowlege...

[QUOTE=the_witch_king]
4.Can i control what he does, like can i allow him only to view stuff and not create directories and files of is own[/QUOTE]
Simple permissions can be set by making the user part of a group with read and execute privileges, and then change the owner of his home directory to someone else and make the permission 550.  That way the user cannot create any files (except maybe in /tmp) and cannot change any permissions.

You can also assign a restricted shell to the user in /etc/passwd by specifying /bin/rbash instead of /bin/bash.  See bash man pages for more info on "RESTRICTED SHELL".

Hope this helps.

---

### Post by the_witch_king on 2006-06-08
> As for the ask yes/no, while you could put that in this same file, the user can control-c out of it and still gain access.  I'm not sure why you would want to interactively allow/deny logins.  If they have the password, they should be allowed to get in.  I think it would become annoying to you to constantly be having to answer the login question, and the user would be forced to wait until you can acknowlege...



 yeah!! you are right it would be very annoying...i just wanted to know if there was someting like in linux for ssh which does what a firewall does in windows. As for the rest , i have to figure out how to add users and stuff first..so i guess once i figure out the basics , i think your info will be more useful. I was thinking more on the lines of what my Sysad does ( i use my college LAN ), i mean i find whenver i login to the department all i can do is basic stuff mail checking ( it basically is a mail account ) ..so i was wondering what you need to do to setup and maintain an account like that..thannx anyways and i would really appreciate it if you could give me some internet resources where i can find out more coz all the resources that i found explain how ssh works, but they don tell me what file to modify and stuff like that...

---

### Post by mbeierl on 2006-06-08
Well, unix security works on the rule of users and groups.  A user can belong to one or more groups, and groups can exist without interactive users.

Files and directories have three permissions: 
1. the owner 
2. the group, and
3. everyone else.

So to restrict users, you simply need to design a schema where the user has access to modify only the files you want them to.  For read and execute access, control that through the group to which they belong.  As for denying access, remove the "everyone else" permission on files you want protected.

The nice thing about ubuntu is it has nice GUIs for more advanced tasks like adding users and groups.  To add a user, simply go through the System -> Administration -> Users and Groups menu and launch that appl.

SSH uses the native users and groups for authentication, so really, it's not a matter of setting up ssh so much as setting up your local users and groups.

The task is even further simplified if you belong to a network which aleady has an authentication server set up, such as an NIS server.

For more information about users and groups, check here:

[http://www.tldp.org/HOWTO/User-Group-HOWTO.html](http://www.tldp.org/HOWTO/User-Group-HOWTO.html)

For more information about linux security, check here:

[http://www.tldp.org/HOWTO/html_single/Security-HOWTO/](http://www.tldp.org/HOWTO/html_single/Security-HOWTO/)

---

