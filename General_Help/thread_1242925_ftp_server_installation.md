---
title: "ftp server installation"
date: 2009-08-17
forum: General Help
---

### Post by ahtasham82 on 2009-08-17
hi guys,

Im new, I need to install ftp server on my online ubuntu server...I am a developer and I need to setup ftp on my server. We have a dedicated server on which UBUNTU 8 is installed. I have installed vsftp and its running...but I cannot connect to my server via FTP...vsftpd is installed and I still cannot connect using my FTP Client...

I really need to set it up...I need your help guys...its very urgent....

looking forward to your quick reply...

Thanks in advance...

Ahtasham

---

### Post by nerdzero on 2009-08-17
Hi Ahtasham,

If you can answer some of these questions, maybe I can help:  

What ftp client are you using?  

What is the error message you receive when you try to connect?  

Is your server behind a firewall?

What happens when you try to connect locally?

---

### Post by ikonia on 2009-08-17
ok - lets get some more info and give you some things to check

1.) what version of ubuntu are you using, ubuntu 8.04 or 8.10
2.) 32bit or 64bit
3.) how did you install vsftpd ?
4.) are you running vsftpd as a stand alone daemon, or via inetd ?
5.) if a standalone server is vsftpd running (ps -ef | grep vsftpd)
6.) if running via inetd has inetd being hupped and configured with ftpd ?
7.) on your machine can you "ftp localhost" this will test if this machine is listening on port 21 with an ftp client.
8.) in the vsftpd config file, look at what interfaces you've told it to listen on, if you've only told it to listen on specific devices or ip addresses - you must use them
9.) check for firewalls infront of the machine
10.) check for host based/local firewalls (iptables -L for example)

that should get you going.

---

### Post by ahtasham82 on 2009-08-17
hi,

first of all...I installed vsftpd but couldnt do it so I uninstalled it...and now installed proftpd...and the answer to your questions are...

I am using filezilla...and trying to connect to the following host.... ftp.firstreleasehomes.com

I get the following error...
Status:    Resolving address of ftp.firstreleasehomes.com
Status:    Connecting to 216.218.175.11:21...
Error:    Connection timed out
Error:    Could not connect to server
Status:    Waiting to retry...
Status:    Resolving address of ftp.firstreleasehomes.com
Status:    Connecting to 216.218.175.11:21...

I dont know whether it is behind a firewall...its a live dedicated server so I believe it must be....

I dont know how to check it locally...

its ubuntu 8.04

I installed proftpd by apt-get install proftpd...and I installed it as inetd

if I do ftp localhost...I get the following...
ftp localhost
ftp: connect: Connection refused
ftp>

I dont know how to check on what interface its listening...


I really need your help...thanks,

Ahtasham

---

### Post by nerdzero on 2009-08-17
So, that tells me that port 21 on ftp.firstreleasehomes.com is not listening for connections.  Does it have to be ftp?  If you can ssh into the server, which I assume you can since you had to to install proftpd, you can just set filezilla to use SFTP.

---

### Post by ahtasham82 on 2009-08-17
why its not listening to 21...I saw the conf file...the port is set to 21 and the proftpd is running...so it should...right ???

also I have to setup ftp because I have to give that info to a client so he can send daily some files to me via that...so I really need to setup FTP....

looking forward to hear back from you....

---

### Post by nerdzero on 2009-08-17
If you are in a hurry, I would just redo your installation and pick standalone this time instead of messing with inetd and its configuration settings.

```
sudo apt-get purge proftpd
```That should get rid of your current install and its configuration files.  Then install again and pick standalone.

I just tried on my server with the standalone installation option.  "ftp localhost" prompted me for my username and password so I'm assuming if I had the proper port open, "ftp <domainname>"  would work from a remote client as well.

When I tried with an inetd installation, I got the same behavior you did so more configuration is required.  I am not familiar enough with inetd to help here.

---

### Post by uDavis on 2009-10-27
For me:
1.) what version of ubuntu are you using, ubuntu 8.04 or 8.10
   The jaunty one
2.) 32bit or 64bit
   32 bit
3.) how did you install vsftpd ?
   sudo apt-get vsftd after the proftp one could never find the package
4.) are you running vsftpd as a stand alone daemon, or via inetd ?
  Standalone
5.) if a standalone server is vsftpd running (ps -ef | grep vsftpd)
   This command returns 27854 24897 0 15:55 tty1 00:00:00 grep vasftpd  I have no idea what it means.
6.) if running via inetd has inetd being hupped and configured with ftpd ?
  No inetd
7.) on your machine can you "ftp localhost" this will test if this machine is listening on port 21 with an ftp client.
   This results in a ftp: connect to address 127.0.0.1: Connection refused
8.) in the vsftpd config file, look at what interfaces you've told it to listen on, if you've only told it to listen on specific devices or ip addresses - you must use them
    Listen=Yes  Anonynous_enable=Yes  local-enable=Yes write_enable=Yes Local_umask=022  connect_from_port_20=yes
9.) check for firewalls infront of the machine
    It's one hop from my desktop to this server. Same subnet.
10.) check for host based/local firewalls (iptables -L for example)
    this is empty with the default Ubuntu server install. I added this in per Sivek pages and do have content for iptables -L -n now

---

### Post by uDavis on 2009-10-27
I read a bunch. and decided to do a reinstall. I did a remove purge of vsftp and a new install. That seems to have fixed the connection refused condition that hung me up for serveral weeks.

It also got rid of the /usr/sbin false positive error message.
A port scanner shows that the FTP port 21 connection service is open.

My next task is to figure out how to create an FTP user and give them permissions to write to the web root area.

thanks  Read a lot... all instructions were helpful even if my frustration index is huge lol.

---

### Post by uDavis on 2009-10-27
The commands that reset and fixed everything.

sudo apt-get remove --purge vsftpd
sudo apt-get install vsftpd

---

