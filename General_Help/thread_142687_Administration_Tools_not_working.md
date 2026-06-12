---
title: "Administration Tools not working"
date: 2006-03-10
forum: General Help
---

### Post by jflash on 2006-03-10
I actually have two problems. They are very similair to the ones listed [here](http://ubuntuforums.org/showthread.php?t=75324). 

My first problem is that I can not access any of the administration tools. This is when I am using the normal user account during setup. As a result, I can't get to the login screen setup to enable root login (I am very new to Linux of any type, so bear with me. That is the only way I know of to login as root). Whenever I try to run an administration tool, I am prompted for a password and nothing happens. No errors or anything. 

My second problem is whenever I try to run ANY sudo command from Terminal. It prompts me for a password. When I try to enter my password, nothing is entered into the field. Afterwards, when I press enter, nothing happens.

As I said, I am very new to Linux (I just installed Ubuntu last night). I installed using Expert mode so I could keep my existing data. If anyone can help me, I would greatly appreciate it. Thanks!

---

### Post by sublime on 2006-03-11
the password you use to login is the password you use to access the root account.  sudo stands for switch user do other.  so when running a sudo command you are temporarily changing your profile to the root user.  this is partly why linux is so secrure.  also when you type in your password when doing a sudo command nothing will show up.

---

### Post by jflash on 2006-03-11
Right, but that dosen't tell me why I can't get the administration tools to work.

---

### Post by z_diver on 2006-03-11
I had this happen the other day.  I had to enable the account in the User and Groups dialog to use administration tools.  This was on an account that was created after the initial installation.  It looks to me like it added my user to the adm: group in /etc/group.  You may try to swich to the root user in a terminal and edit /etc/group by using the command sudo su.

Edit: sudo su should get you to the root user in a terminal.  Then use gedit /etc/group to edit the file.

---

### Post by jflash on 2006-03-11
[QUOTE=z_diver]You may try to swich to the root user in a terminal and edit /etc/group by using the command sudo su.

Edit: sudo su should get you to the root user in a terminal.  Then use gedit /etc/group to edit the file.[/QUOTE]

I think I mentioned before that whenever I try to do _anything_ using sudo in terminal, at the password prompt it won't take my entry (as in, nothng is shown after the 'Password:' line after I enter my password).

EDIT: In case it helps, here is a screenshot I took after attempting to enter my password and pressing enter. As you can see, nothing is in the 'Password:' field because it wouldn't accept any input:

[IMG]http://i19.photobucket.com/albums/b189/ki4hrg/Screenshot-1.png[/IMG]

EDIT2: Whenever I have just logged on, or my system has been idle for a while, whenever I try to access an administration tool, I am prompted for my password. My login and root password are the same, so there are no problems there, but I get nothing after entering it.

---

