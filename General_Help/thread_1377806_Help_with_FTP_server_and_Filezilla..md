---
title: "Help with FTP server and Filezilla."
date: 2010-01-10
forum: General Help
---

### Post by venividibitchy on 2010-01-10
I installed vsftpd and edited the config. file according to the instructions. I restarted the process. I then installed FileZilla.

I input 127.0.0.1 as my host name, my username and password, and port 21. Connection is successful for a few minutes until I get a 421 Timeout and the connection closes.

While still connected, I have attempted to run the network configuration wizard, only to find a few hitches. The furthest I got was when I had the wizard acquire my IP address from the website (I do have a dynamic IP), and when I manually input port 50000-50050 for it to use, because I have forwarded them on my router. The test gets quite far, and only fails at this juncture:
Response: 150 opening data connection
Response: 503 Failure of data connection.
Server sent unexpected reply.
Connection closed

What could be going on? I double-checked that my ISP allows FTP on port 21, and all seems good to go.

---

### Post by venividibitchy on 2010-01-12
Bump.

---

### Post by Enigmapond on 2010-01-12
Why are you putting the loopback to your computer as a host? The host should be where you want to connect to i.e ftp.blahblah.com. I'm confused. I also use filezilla but find gftp easier and lighter weight.

---

### Post by pricetech on 2010-01-12
Just to clarify;  Is your goal to set up and FTP server which will be accessible over the Internet ??

---

### Post by venividibitchy on 2010-01-12
> **pricetech said:**
> Just to clarify; Is your goal to set up and FTP server which will be accessible over the Internet ??

Yes, my goal is to set up an FTP server using my own home network as a host.

> **Enigmapond said:**
> Why are you putting the loopback to your computer as a host? The host should be where you want to connect to i.e ftp.blahblah.com. I'm confused. I also use filezilla but find gftp easier and lighter weight.

Sorry to be confusing. This is my first time setting up an FTP server.

I guess I assumed I'd use 127.0.0.1 through process of elimination. Should I be using my internal or external IP address, instead? I don't know what else to put in as "host".

The Lifehacker website recommended using localhost (127.0.0.1) and port 14747, but Filezilla refuses to connect with this. Only 127.0.0.1 and port 21 work...temporarily.

---

### Post by Enigmapond on 2010-01-12
Ok the loopback would be wrong then. You need to know the address to your router. Normally it's something like 192.168.1.1 but you will need to configure or forward the ports you will be using. Also you need to be sure you have the server version of Filezilla. I did a little research and found this : [http://www.instructables.com/id/Setting-up-an-FTP-server-using-filezilla/](http://www.instructables.com/id/Setting-up-an-FTP-server-using-filezilla/) 

This isn't an Ubuntu problem but just proper settings for Filezilla and your ports. I hope this helps.

Cheers!

---

### Post by venividibitchy on 2010-01-12
> **Enigmapond said:**
> Ok the loopback would be wrong then. You need to know the address to your router. Normally it's something like 192.168.1.1 but you will need to configure or forward the ports you will be using. Also you need to be sure you have the server version of Filezilla. I did a little research and found this : [http://www.instructables.com/id/Setting-up-an-FTP-server-using-filezilla/](http://www.instructables.com/id/Setting-up-an-FTP-server-using-filezilla/) 

This isn't an Ubuntu problem but just proper settings for Filezilla and your ports. I hope this helps.

Cheers!

Yep, 192.168.1.1. I already forwarded port 21, and then 50000-50100.

I didn't have the server version -- that could've been the problem. Unfortunately, there doesn't appear to be one for Ubuntu.

---

### Post by Enigmapond on 2010-01-12
Unfortunately I am not that familiar with setting up a server, there is documentation here that also may be of some help.
[https://help.ubuntu.com/community/FtpServer](https://help.ubuntu.com/community/FtpServer)

Cheers!

---

### Post by venividibitchy on 2010-01-12
> **Enigmapond said:**
> Unfortunately I am not that familiar with setting up a server, there is documentation here that also may be of some help.
[https://help.ubuntu.com/community/FtpServer](https://help.ubuntu.com/community/FtpServer)

Cheers!

Thanks-

I followed the instructions on that page, only to find that I already had a user named "FTP". I added the home directory, though.

I tried following instructions on [this page]("http://www.wikihow.com/Setup-vsftpd-FTP-on-Ubuntu-Linux"), but it doesn't detail whether it can work as a SERVER, nor how to proceed once everything is installed/configured.[]("http://www.wikihow.com/Setup-vsftpd-FTP-on-Ubuntu-Linux")

---

### Post by pricetech on 2010-01-14
If you followed the steps from the Ubuntu manual, your FTP server should work just fine using vsftp.  I've never had a problem with it yet.  Just make sure you understand the difference between anonymous and authenticated and remember above all that FTP is NOT secure.

If you want security, set up SSH and use SFTP.  There's a winders client available (winscp) that works just fine if you're connecting using winders boxen.

---

### Post by Saiko Berry on 2010-01-14
Just in case you wern't aware you can do most FTP things directly from terminal.
> ftp
> open location
> username prompt
> password
help for commands.

---

