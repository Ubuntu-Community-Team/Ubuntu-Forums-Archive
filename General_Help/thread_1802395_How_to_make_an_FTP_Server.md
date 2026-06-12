---
title: "How to make an FTP Server"
date: 2011-07-11
forum: General Help
---

### Post by Gr72 on 2011-07-11
Hey Guys,
I didn't know whether or not to put this in the "General Help" category or "Server Platforms" So I put it in the General Help. But, to get to my question, I would like to make an SFTP Server that's connected to a domain name. I would like to be able to go to a website and access files on my server from anywhere but I don't know where to start. Any help with this would be wonderful. 
Thank You Guys In Advance
-Gr72-

---

### Post by enimeizoo on 2011-07-12
I think ftp and sftp are actually two very different servers. They serve the same purpose, but sftp is merely a ssh server with some options.
I would advice for a sftp server, unless you keep it local.
You will find some howtos by googling around. [Here]("http://www.brennan.id.au/16-Secure_Shell.html") is one.

---

### Post by JedMeister on 2011-07-13
And it is available via SSH (where is it referred to as SFTP). Or it can be transported over SSL (where it is referred to as FTPS). Or can be unsecured (and called just FTP). Technically they're all FTP but SFTP and FTPS are secured as well.

SFTP is really easy to set up. Install OpenSSH and it's there! FTPS can be done may different ways although the package of choice seems to be VSFTPd. Install info and config for both can be found in the Ubuntu Server Guide.

AFAIK both systems rely on normal Linux user accounts. The added benefit (or disadvantage depending on what you are trying to acheive) of SSH is that it also gives you shell access. If you want to avoid that and/or create user chroot gaols then VSFTPd is probably the better option.

---

### Post by Lars Noodén on 2011-07-13
SFTP is the way to go because it is secure and FTP is not.  SFTP requires no additional configuration, FTP is hard to configure.

SFTP is provided as a built-in component of the package OpenSSH-server.  By installing the package, you have SFTP ready to go automatically.  If you don't want to allow SSH access at the same time, then you can restrict some accounts to be [SFTP-only](http://en.wikibooks.org/wiki/OpenSSH/Cookbook/SFTP#SFTP-only_Accounts).

---

### Post by Gr72 on 2011-07-13
thanks for the replies guys. But what I also want to know is how to set up a website w/ a login and a GUI to download and upload files.

---

### Post by enimeizoo on 2011-07-13
A web server is another thing. It needs way more attention. 
The simplest setup is an apache server, but then you might find yourself limited and install php and mysql.
This also require the knowlege of 2 languages (html and php), and possibly a little bit of knowlege about databases.

I didn't set up one open to the internet, yet, so I really should let more experienced people answer this :P

---

### Post by Lars Noodén on 2011-07-13
> **Gr72 said:**
> thanks for the replies guys. But what I also want to know is how to set up a website w/ a login and a GUI to download and upload files.

There are plenty of [GUI clients for SFTP](http://en.wikibooks.org/wiki/OpenSSH/Client_Applications#GUI_Clients) to choose from.  They can be used to upload and download files to/from the server.

---

### Post by Gr72 on 2011-07-13
ok, so I understand that the website needs scripting behind it to do the actions. do they have any scripts out there that I can use until I design my own. and I don't have a dynamic IP so would I have to use DynDNS to keep IP's straight?

---

### Post by JedMeister on 2011-07-14
A webserver and an (S)FTP(S) server are different things. A webserver serves content using http and ftp is for file transfer. You can have both installed on the same physical server but they are 2 completely different functions.

If you intend to have only people you trust using your server, go with SFTP (from *openssh-server* package as mentioned previously) because it will require much less config. 

But if you intend to have people you don't know and/or don't completely trust then I would suggest you use FTPS (just as secure but uses SSL - like https sites do, rather than SSH). The package to install is *vsftpd* It's a little more involved to setup than SFTP, but it is more flexible and is easier IMO to configure to limit user's access.

As for a general Website you'll probably want a LAMP setup (Linux Apache2 MySQL and PHP). You can configure your own from scratch but I suggest you have a look at Turnkey Linux (TKL) [LAMP appliance]("http://www.turnkeylinux.org/lampstack"). It available as a VM image or an ISO and is basically a custom Ubuntu 10.04 LAMP stack with a few added extras: It has SHH/SFTP installed and preconfigured by default, it has a Webshell interface (Web based commandline access) and Webmin (a Linux sysadmin WebUI) as well as having phpMyAdmin (MySQL admin WebUI).

---

### Post by Lars Noodén on 2011-07-14
> **JedMeister said:**
> ...But if you intend to have people you don't know and/or don't completely trust...

In that case, it is very easy and very secure to use [chrooted SFTP](http://en.wikibooks.org/wiki/OpenSSH/Cookbook/SFTP#Chrooted_SFTP-Only_Accounts).  That allows them to login and upload or download, but neither shell login or access outside of their directory.  It's very easy to configure.

---

### Post by JedMeister on 2011-07-17
> **Lars Noodén said:**
> In that case, it is very easy and very secure to use [chrooted SFTP](http://en.wikibooks.org/wiki/OpenSSH/Cookbook/SFTP#Chrooted_SFTP-Only_Accounts).  That allows them to login and upload or download, but neither shell login or access outside of their directory.  It's very easy to configure.Yes you can do that but IMO it's much easier to set up chroots using FTPS using VSFTPd than it is chroot gaols with SFTP and there are a couple of bugs and/or strange behaviours with SFTP chroots (at least in Lucid anyway). But each to their own :)

---

