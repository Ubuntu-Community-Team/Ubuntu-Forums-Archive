---
title: "Pure-ftpd - 530 Athentication error access denied"
date: 2011-03-25
forum: General Help
---

### Post by spindler on 2011-03-25
I am having difficulties with Pure-FTPD.    I had it working at one time.  I recently had to reinstall Ubuntu 10.10 because pure-ftpd stopped working for some reason and now I have a fresh install but pure-ftpd still does not work.

This is what I did to install it. 

Sudo apt-get install pure-ftpd

Using the Ubuntu Spftware Center I installed PureAdmin.

I then create a virtual user.

Then in the terminal entered the following:

 [FONT=&quot]Sudo ln –s /etc/pure-ftpd/conf/PureDB /etc/pure-ftpd/auth/45puredb[/FONT]
  [FONT=&quot]Sudo gedit /etc/pure-ftpd/conf/PAMAuthentication[/FONT]
  [FONT=&quot]   Change yes to no[/FONT]
  [FONT=&quot]Sudo /etc/init.d/pure-ftpd stop[/FONT]
  [FONT=&quot]Sudo /usr/sbin/pure-ftpd –j –lpuredb:/etc/pureftpd.pdb &[/FONT]
  [FONT=&quot]Sudo /etc/init.d/pure-ftpd  start[/FONT]
  
When I attempt to access the server using filezilla I get the following:

Status:    Connecting to 100.247.180.140:21...
Status:    Connection established, waiting for welcome message...
[COLOR=Green]Response:    220---------- Welcome to Pure-FTPd [privsep] [TLS] ----------
Response:    220-You are user number 1 of 50 allowed.
Response:    220-Local time is now 11:28. Server port: 21.
Response:    220-This is a private system - No anonymous login
Response:    220-IPv6 connections are also welcome on this server.
Response:    220 You will be disconnected after 15 minutes of inactivity.[/COLOR]
[COLOR=Blue]Command:    USER test[/COLOR]
[COLOR=Green]Response:    331 User test OK. Password required[/COLOR]
[COLOR=Blue]Command:    PASS ********[/COLOR]
[COLOR=Green]Response:    530 Login authentication failed[/COLOR]
[COLOR=Red]Error:    Critical error
Error:    Could not connect to server[/COLOR]

I read somewhere that this could be a filezilla issue and to fix it I need to use active mode and use the filezilla external address  [http://ip.filezilla-project.org/ip.php](http://ip.filezilla-project.org/ip.php)

Of course I did this and the filezilla solution did not work this time.  I am fairly sure it is a server issue this time.

Any ideas?

---

### Post by Script Warlock on 2011-03-25
maybe you supplied a wrong username, password or host..

---

### Post by spindler on 2011-03-25
Well that is useful.  At first I thought this could not be the case.   I guess the error log is deceptive when it displays a user name and password error. 

So now I am wondering how I can be getting the wrong user name and password. I attempted a 2 or 3 users and found that only the administrator name and password was able to login.

The admin user points to the directory  /home/Admin

the Admin user is a member of group admin (1000)




Using PureAdmin, I have set up a virtual host user name and password to point to the following:

home directory   /home/ftp      (folder owner> ftpuser:ftpgroup)
user ID: ftpuser(115)
Group ID: ftpgroup (124)

I also tried a system user.  I am not sure where it is pointing to.  If it is pointing to the home/user directory then the ftp configurations might not work as the over of the directory is user:user.

I also set up a virtual user to point to my system user and gave it the following:

home directory :  /home/user
User ID: user (1002)
Group ID: ftpgroup(124)

I gave the user ID of user so the virtual user could have the same permissions as the system user.

Is there a correct way to set up the virtual server that I do not know about?

---

### Post by lrdfrtd on 2012-05-25
i have the same problem ](*,) i had it fixed once but now i dont remember how to do it, it had something to do with a bug in the server, it will allow actuall users of the system to connect but not any with permissions of 1000 or lower such as (ftpuser/ftpgroup) this is more of a bug on "pureadmin's " side because the server works this way but the pureadmin wont, if u edit the group/user permissions then pureadmin wont work but the server will, i remember i had to edit the server to accept users of rank 1000 or less (i set mine to 1) so they both worked but i cant remember what i had to edit..  DAMN U ppl thanks for your effort but plz stop sending out untested builds #-o
(im runing ubuntu server 12)

Edited:
So i figured it out 
(fresh install)

1. sudo apt-get install pureadmin
(pure-ftpd comes with the pureadmin install)
if you dont use pureadmin just do step 2 

2. sudo gedit /etc/pure-ftpd/conf/MinUID

Set value to 1  (not1000)
this will let you login users with rank 1-999999999  instead of 1000-9999999999 sadly this is less secure because some system "users" dont have passwords so just chmod jail to a blank dir

3. sudo ln -s /etc/pure-ftpd/conf/PureDB /etc/pure-ftpd/auth/50pure

and of course after you make those changes 
4. sudo service pure-ftpd restart

---

### Post by oldos2er on 2012-05-25
Old thread closed.

---

