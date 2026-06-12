---
title: "New user's scroll keys don't work"
date: 2011-10-25
forum: General Help
---

### Post by Bradburts on 2011-10-25
Ubuntu Server 10.04.3
I created a new account:-
 
[FONT=Courier New, monospace]sudo useradd -d /home/newuser-m newuser[/FONT]
[FONT=Times New Roman, serif][SIZE=1]Add a password:-[/SIZE][/FONT]
[FONT=Courier New, monospace]sudo passwd newuser[/FONT]
 
When I login to the new account the cursor keys display escape codes, up/down doesnt navigate history.
echo $HISTFILE returns blank.
.bashrc is the same as my regular account. Noticed that .bashrc exits if the shell is not in interactive mode.
 
Seems like this should have a simple solution but I cannot find it!
 
EDIT:
PS I am using SSH with Putty. Have not tried the console yet. 
There are no difference between this account's .profile/.bashrc and the initial account so I am guessing permissions but cannot find it!

---

### Post by Bradburts on 2011-10-26
Anyone?
Its just a basic 10.04 server install with openssh & so I think this has gotta be a simple case.....
Well I'm hopping anyway!

---

### Post by Bradburts on 2011-11-02
```
addduser newuser 
```
works ok & creates the required directories.
 
I think that if you specify too many options you end up creating a system user and that may explain the missing shell.

---

