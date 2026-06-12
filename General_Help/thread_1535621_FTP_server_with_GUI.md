---
title: "FTP server with GUI"
date: 2010-07-21
forum: General Help
---

### Post by Xi0N on 2010-07-21
I am going to install an FTP server on a headless server running ubuntu.

The thing is that i want to be able to manage it completely via a web interface or a remote gui from any other system.

The idea is that the manager of the accounts of the ftp could do his tasks without having to ssh into the server or anything (since he will completely ignore its a linux system and he does not need to know how to use it or log in or whatever)

Is there any way to manage an ftp server like this?

Thanks!!

---

### Post by HermanAB on 2010-07-21
On Ubuntu, Webmin is the way to go.  Other more mature distros have wizards for it, but here you are not so lucky.

---

### Post by thebigob on 2010-07-21
Even though your server is headless you can install X on it.

Using ssh you can forward X using 

ssh -X example.server.com

This will allow x forwarding via ssh

When you type a command that has a gui it will be sent to the remote machine. 

eg

ssh -X example.server.com

gedit

gedit will appear on your screen.

---

### Post by Xi0N on 2010-07-21
Thanks for the reply! :)

Ok, this leads to two questions: First...... an example of a distro that has this gui for ftp?

And the other: If i redirect the X gui of a program for managing the FTP server, which would this program be?
I mean... is there any linux ftp server that includes a gui for user management? if so, my problem would be solved :)

Thanks!!

---

### Post by christiansale on 2010-07-21
First of all , i&#39;m new here , and i&#39;m working with Linux 4 a year now (first Mandrake now Suse 9.1 pro)

I&#39;m afcourse very satisfied about Suse...

...but i&#39;m still a newbee... So i need those GUI&#39;s. (like Yast) [IMG]http://forums.opensuse.org/images/smilies/biggrin.png[/IMG] 

I&#39;ve got Apache2 and serveral P2P clients running.

---

### Post by christiansale on 2010-07-21
First of all , i'm new here , and i'm working with Linux 4 a year now (first Mandrake now Suse 9.1 pro.I'm afcourse very satisfied about Suse.but i'm still a newbee... So i need those GUI's. (like Yast) I've got Apache2 and serveral P2P clients running.

---

### Post by thebigob on 2010-07-23
There are loads with gui's but something like filezilla comes to mind.

---

### Post by Xi0N on 2011-03-28
I did not touch this subject for almost a year.... i have been playing around with xming.... which helps a bit for having a wider range of ideas about the solution to the problem i pictured...
But i still would prefer a web UI for "dummies"...... any new thoughts? Even VirtualBox has a web UI!! (Which works perfectly, BTW... :P)

---

### Post by Vishal Agarwal on 2011-03-28
There are different ftp servers available for ubuntu. I am using vsftp server. After installing it you can access the user home folders through internet explorer in read only mode with the following url:

[ftp://servername](ftp://servername)

---

### Post by Xi0N on 2011-03-28
Yes, but what I want is to manage the users and accounts of the ftp server.

Create a new ftp user
Administrate the permissions
View the current transfers from/to the ftp server

There are thousands of them for windows, with their guis and so.. and I think its quite strange there is no one for linux, via web.....

---

### Post by newbuntuxx on 2011-03-28
I don't think there are GUIs for ftp servers on ubuntu. Some one mentioned webmin, this is an over kill if you just want a gui for ftp server.

I think i've seen a small gui config wizard on redhat, where basically it presented you with all the options in the vsftp.conf file in a gui format.

---

