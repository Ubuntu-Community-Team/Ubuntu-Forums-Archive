---
title: "POSSIBLE SECURITY THREAT leaves Ubuntu wide open"
date: 2010-07-22
forum: General Help
---

### Post by patdundee on 2010-07-22
Hi Guys
 
Ubuntu 9.04 Jaunty (Server)
 
I was alerted to a rouge phishing page on one of my clients web sites which they new nothing about. This page had been placed into many of their websites root folders and had to be removed.
 
On checking all of their folders I actually came accross a tar file which had created a masterpiece of a page. With this page once in place the user could open this page up and break out of the root directory for the site and traverse all the way up to the main root on the server. It can also run commands add and remove pages to wherever it wants and much much more including execute and kernal commands direct on the server. 
 
I have attached some screen shots of the page for you to look at.
 
If anyone from the Ubuntu team would like to have a look at this page with the full code I will be more than happy to send it to you. the page is written in PHP and is a major security threat I would presume to any one running Linux based servers.

---

### Post by dcstar on 2010-07-22
> **patdundee said:**
> Hi Guys
 
Ubuntu 9.04 Jaunty (Server)
 
I was alerted to a rouge phishing page on one of my clients web sites which they new nothing about. This page had been placed into many of their websites root folders and had to be removed.
........

This is a user support forum, if you have found an Ubuntu package that contains a security problem then use the bug reporting process that already exists.

If people leave their servers open to allow people to upload malicious code onto their web sites then that is a basic security problem for those who maintain the web site.

---

### Post by patdundee on 2010-07-22
Hi Dc
 
Yes there is a bug reporting system but this is also a general help forum. Some users may not be as good as others with the server edition and surely would be pleased to be informed of things that can cause issues for them. Hence the post on here.
 
My Server is set up correctly and people are locked in directories when FTP is in use. Access to the server is restricted to port 21 and 80 there is no SSH or other access to the server. and the groups and permissions are also set up correctly. Still this PHP page can break through and do as it wishes.
 
Therefore the post is also on here for anyone else who would like to know about it.

---

### Post by iponeverything on 2010-07-22
Curious about some things:

php config, version
apache config, version
mysql config, version
kernel version
have you run debsums?
what are the php applications currently in use on the machine? 
Is there a root kit on the box now?
Was the box up to date?
What other services are running on the machine?

Do you have the logs to see if the the initial compromise might have a bad password chosen by one of your clients where black hat used a local escalation to fixup php?

BTW -- It very premature to use that subject line. Your box may have been compromised though a configuration error or by the mistake of one of your clients -- to assume that "Ubuntu wide open" is wrong.

---

### Post by WorMzy on 2010-07-22
httpd/apache is run as the http user, I fail to see how a PHP script would gain access to the root of the host machine without su-ing into root, which is impossibly on Ubuntu (unless you set a password for root before hand), or by using sudo, which the http user isn't registered to use by default.

Could you elaborate on how this script works?

---

### Post by iponeverything on 2010-07-22
> **WorMzy said:**
> httpd/apache is run as the http user, I fail to see how a PHP script would gain access to the root of the host machine without su-ing into root, which is impossibly on Ubuntu (unless you set a password for root before hand), or by using sudo, which the http user isn't registered to use by default.

Could you elaborate on how this script works?

It is easy for a PHP script to gain access though PHP or Apache misconfiguration.

---

