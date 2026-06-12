---
title: "SUDO (is it another user has a root privilege ?)"
date: 2006-03-07
forum: General Help
---

### Post by mbb on 2006-03-07
Hi everyone, 
I have some questions about sudo command, it made me confused alittle bit.
First of all, I wanna indicate that I am not a newbie to linux world, I have been using linux(slackware,mandrake,redhat and suse) distros for 3 years. I am not an expert either (just an average user want to learn much :) ).
Please refer me a link to read more about sudo in detail.

I have a problem with sudo command, because I have been using suse for a long time  . I used to have two different users like root and myself. The problem started when I try to sepereate the user (myself) from root. I set a password to root part (I forgot the command line here, I had googled for it, I didn't write it down :) ). Ohh bye the way I am using 5.10 version of ubuntu (2 days :) ). 
Right now I have a user password and root password,, however when I use sudo command it sometimes accept user password sometimes root password. (???)

Another problem that I encounter right now is, I cannot access  a program that I install manually (./configure make sudo make install) (the program was grace )by both as a user and as a root( I use su - command to pass root side).  I need to write (sudo xmgrace) again to access to program.  

How can I change it ?
waiting for your helpful responses... :)
mbb

---

### Post by colo on 2006-03-07
sudo (normally) is just a way to grant "normal" users limited root-privileges for certain commands. In ubuntu, it's used to not have the average Joe User remeber TWO passwords, instead of one. If you don't like that conecpt, and prefer using "su" exclusivley to switch user contexts, you may want to issue "sudo passwd root", to set a permanent password token for root in your /etc/shadow, and enable login for root. This has some security implications, but they can be considered negligible.

sudo is configured to ask for the password of the normal user when elevating his or her privileges to root. So if the passwords of your user and root do not match, you're supposed to enter the password of the UNPRIVILEGED user, NOT an eventually set root-password.

The problem with your self-installed program lies within it's Makefile, I suppose - the "install"-rules is possibly farked somehow. Chances are very little that there actually went some something wrong when installing it on YOUR particular system. You might want to check whether the directory of the application's binary in your normal user's "$PATH", however.

Hth.

---

