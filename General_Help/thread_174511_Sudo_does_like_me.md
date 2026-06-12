---
title: "Sudo does like me"
date: 2006-05-11
forum: General Help
---

### Post by Lamorue on 2006-05-11
Good day everyboday

ubuntu Breazy Badger 5.10

I made a new install on a new hard disk and I realised that my problem was not realy my password but sudo who does not respond to my commands because when I give an erronous password he tells me but with the right password he goes back on the propt again but no action taken

I have tried this


[PHP]lamorue@ubuntu:~$ sudo update 
Password: 
Sorry, try again. 
Password: 
lamorue@ubuntu:~$ sudo upgrade 
lamorue@ubuntu:~$  [/PHP]


I also tried that


[PHP]lamorue@ubuntu:~$ sudo apt-get update && sudo apt-get upgrade 
Password: 
lamorue@ubuntu:~$  [/PHP]

With these commands on both of my HDD no answer no downloads no windows nothing

I just tried tu use add application from the menu and it says and I translate :


[PHP]Echec lors du lancement de /usr/bin/gnome-app-install avec l'utilisateur root :

Child terminated with 1 status  [/PHP]

Translation : Failure when launching ... ...with user root :

I am a novice on Linux
Please I need help to solve that problem 

Where is the problem and how can I solve it

Thank you in advance 
lamorue

---

### Post by nanotube on 2006-05-12
hmm, maybe your user does not have sudo privileges? 
did you by any chance do an "expert" install?

check and see if your user is a member of group "admin" (look at file /etc/group).

---

### Post by Lamorue on 2006-05-12
Thank you nanotube

I have check your command 

> lamorue@blueberry:~$ /etc/group
bash: /etc/group: Permission non accordée
lamorue@blueberry:~$

Translation : permission denied

What I can do from now ?

Thank you for your documentation

Lamorue

---

### Post by Gustav on 2006-05-12
open the file with an editor by typing:```
gedit /etc/group
```
(when you do as you do you try to run the file as if it is a program or script)

---

### Post by Lamorue on 2006-05-12
Thank You Gustav

I have tried to send you the list of the command gedit /etc/group
But an error mrssage comes up

 >   1. You have included 53 images in your message. You are limited to using 8 images so please go back and correct the problem and then continue again.

      Images include use of smilies, the vB code [img] tag and HTML <img> tags. The use of these is all subject to them being enabled by the administrator.
I have entered the command in the terminal and here is the asswer

Whatt should I do from that ?

Thank you  Lamorue

---

### Post by dg_w on 2006-05-12
try:
Logout of gnome 
-- then
CTRL+ALT+F2
login as usual
sudo apt-get update
 when prompted put in your password again..

What do you get now ?

---

### Post by Mustard on 2006-05-12
Try this HOW TO to check if you have sudo set up correctly..


Use the **'Recovery Mode'** from the Grub menu at startup.

Recovery mode will drop you to a root prompt.  If you don't see the GRUB menu at startup then you probably have to press the ESC key to view it, as its sometimes hidden and only revealed when you hit the ESC key.

Once at the root prompt you can use this command to edit the /etc/sudoers file..

```
visudo  #this command does on thing.  It opens the sudoers file for editing
```

**Note**:- To save the sudoers file from visudo after editing you would use **ctrl + o**.  To exit visudo use **ctrl + x**.

My sudoers file looks like this.  Note the last line where I give my user sudo privileges.  This is the line that would need to be added by those who, for whatever reason, don't have sudo privileges.

```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL
mustard ALL=(ALL) ALL

```

**Method 1. Adding your username directly to sudoers**

You can see my username on the bottom line.  You would need to add your username to the bottom as I have done.

Assuming your user name was "bob'', then the line that would need to be added would be..
```
bob ALL=(ALL) ALL
```

This is just one way of doing it.

**Method 2. Adding a user to the administration group**
Note:If you are going to use this method, please ascertain whether an administration group is already set up.  See instructions below for viewing all the groups on your system.

Some sudoers files are set up with an admin group called 'adm' or sometimes it is called 'admin' (it can be called whatever you like really, but these two are fairly intuitive).  Users are then added to the adm group, and a line in the sudoers file that looks like this below gives members of the 'adm'  group admin access.

```
%adm ALL=(ALL) ALL
```

If your group is called 'admin' then it would look like this

```
%admin ALL=(ALL) ALL
```

You can find out what groups are setup on your system with this command..

```
cat /etc/group
```

If you decided to do it this way you would create the line above at the bottom of your sudoers file, using one of the examples above, save the sudoers file,  then at the root prompt do this command (substituting your username in the appropriate place and whatever your administration group is normally called)..

```
adduser your_username adm
```

or for the case of 'admin' being your administration group..

```
adduser your_username admin
```

---

### Post by Lamorue on 2006-05-14
Thank you Mustard
Thank you all

Problem solved

I have tied the first solution on my first HDD and worked fine

I thried the second solution on my second HDD and I had a problem so I tried the first solution and it work fine. On that HDD I will restart a new install because too many problems : Sound ,Printer, etc...

But on my first HDD when I made my first update linux did not ask me for password but after he was asking me for one and did not work. The rmaining problem so far if it is a problem and that append only after my first update when I press escape to go in recovery mode it seams that i have two installation because I have two choise like this:

[PHP]ubuntu, kermel 2.6.12-10-386
ubuntu, kermel 2.6.12-10-386 (recovery mode)
ubuntu, kermel 2.6.12-10-386
ubuntu, kermel 2.6.12-10-386 (recovery mode)
ubuntu, mem+est86+[/PHP]

Tell me is that a source of problem or not?
Should I reinstall.

Thank you
Lamorue

---

### Post by Mustard on 2006-05-14
Are you sure the numbers for the kernel versions are **exactly** the same?

It's quite common for an older kernel version to be in the grub menu after a kernel update.

---

### Post by Lamorue on 2006-05-14
Mustard

You are wright I made a mistake there is a difference in the two numbers :

> ubuntu, kermel 2.6.12-10-386
ubuntu, kermel 2.6.12-10-386 (recovery mode)
ubuntu, kermel 2.6.12-9-386
ubuntu, kermel 2.6.12-9-386 (recovery mode)
ubuntu, memtest 86+

I always use the same version which as been verified with MD5Checker and my cd has been verivied for mistake. 

I made adout 4 install before to get my first install working I always get a lot of problems with my password every time he does not like my password and always have to add it after with adduser.

I even had problems with the root password and ask me again near the end of the installation to reenter my root password again because he sais it was no good and reentry the same password and accepted it. 
Very often he tells me that my password is empty I dont know watt he means. 
My root password is( 5 letters folloded bu 4 numbers ) Logging name is ( lamorue ) and my password is ( paspebia ) Is there any problem with those names?. 

If I remember well all the names he ask:

> 1) my full name  ( Which has french accent with capital letters and space between first and second name. That shoul not matter and thats watt they suggest. )

2 )my first name with small letters only ( thats watt they suggest but to me it did not look like it was the root password )

3 ) password  ( and they suggest to have letters numbers and ponctuation caractors. To me it the root password )

3 ) my logging name 

5 ) my logging password

Is that right whatt I am saying ?

May be the language has something to do with it  but I am very carefull not to enter any french caractor in it. Even the language It's the same sofware that you choose language at start up.

I am planning to download a new copy and give an other try.

If you have any suggestion for me befor i make a new install will be very appreciate.

Thank you very mutch for your help it was a big relief to be able to updte after so long

Thank you 
Lamorue

---

