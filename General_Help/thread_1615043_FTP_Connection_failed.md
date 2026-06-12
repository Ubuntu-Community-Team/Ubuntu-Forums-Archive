---
title: "FTP Connection failed"
date: 2010-11-06
forum: General Help
---

### Post by spindler on 2010-11-06
Hello,

I am attempting to upload some information onto my UBUNTU machine using a FTP connection.   I am going through a router which I configured to forward port 21 to the Ubuntu machine.

I have not been able to test if the port is set up correctly or not.   Anyone know how I can do this?

What I am doing is attempting to upload a plug in for a word press website.   Upgrading the plug in is done from within word press and it uses ftp.   I tried upgrading the plug in from the Ubuntu machine  as well as from another machine on my network.

......Of course it is easy enough to just download the plug in and install it directly into the folder....however, this would not fix my FTP connection problem.

So my questions again are:

1.  Does any one know how I can test my FTP connection?  Maybe my router is configured wrong?
2. Do I need to configure anything on my UBUNTU Machine to accept FTP requests?

Thanks,
Spindler
....by the way Spindler died a while ago....  X-(

---

### Post by holiday on 2010-11-06
I don't think FTP server is in the default Ubuntu install. 

Check firewalls on client and server.

Also - FTP actually uses two ports. 21 is the control port and 20 is the data port.

However, if you're configuring your router to accept FTP from the internet then you should consider SFTP instead. 

Seriously.

---

### Post by gnush on 2010-11-06
Hello Spindler.
You should be able to scan your router for open ports using a port scanning such as _[nmap]("http://nmap.org")_.
I'm not sure what you're doing to establish an FTP connection to your computer, but you'll have to have a server (_[pureftd]("http://en.wikipedia.org/wiki/Pure-FTPd")_ for example) running on the computer you want to connect to.

---

### Post by spindler on 2010-11-06
Ok....

This is news to me.  I did not know I needed an FTP server on my Ubuntu machine.  Thanks a lot.

I will also look into SFTP.  This looks like a good idea.

I will do something with this and see what happens.

Thanks,

Spindler

---

### Post by spindler on 2010-11-06
Hello Everyone,

I was able to install   PROFTPD.   I found some information on how to configure the software here.

[https://help.ubuntu.com/community/ProFTPD](https://help.ubuntu.com/community/ProFTPD)

I was able to test my router...sort of....   I pointed to a different computer on my network and started the word press ftps  file transfer .  The browser then opened the default web page for that computer.  I am fairly confident my problem is on the Ubuntu machine.

When I try to upload a file onto my Ubuntu machine I cannot make a connection. 

Using the wordpress browser based FTP , I keep getting a message stating   "Failed to connect to FTP Server   {websitename}:21

I also tried using FILEZILLA to connect as well and I am getting the following message:

Status:       resolving address of .........
Status:       Connecting to xxx.xxx.xxx.xxx:21
Status:       Connection established, waiting for welcome message.....
[COLOR=Red]Error:        Could not connect to server[/COLOR]
Status:        Waiting for retry.....

Any ideas why the PROFTPD  might not be working?

What else might be the problem?

Thanks,

Spindler

---

### Post by holiday on 2010-11-06
Install ssh on your Ubuntu machine.

Follow these simple instructions:

[https://help.ubuntu.com/10.04/serverguide/C/openssh-server.html](https://help.ubuntu.com/10.04/serverguide/C/openssh-server.html)

Unless you've set up a DMZ, do NOT open your network to FTP from the wilds. And if you don't know what DMZ means then for sure you haven't set one up.

---

### Post by spindler on 2010-11-06
Hello Holiday,

You are forever concerned about security.  This is always good.  Thank you for the help.

However, I still cannot access my computer through FTP.   Any comments on this specific problem?

Thanks,

Spindler

---

