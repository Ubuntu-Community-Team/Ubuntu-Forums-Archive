---
title: "Help me decide on my &quot;Home Server&quot; Ubuntu vs Windows etc"
date: 2012-09-09
forum: General Help
---

### Post by b18turboef on 2012-09-09
I truly love Ubuntu for many reasons, but to be honest I've grown up using Mac and Windows and know both of them MUCH more extensively.  That being said I like the idea of running my home server on a reliable platform.  More or less its a plenty capable little computer with a 2tb drive.  The ONLY use I care about is I'll be running "crashplan.com" software to backup my windows 7 desktop (possibly other computers but that makes no difference with the software). 

My question to you is, assuming windows 7 professional was free like ubuntu, which OS would you use for a little computer sitting and doing nothing but backups?  Maybe in the future it will host my media files etc.  I want simplicity and ease of use.  But I do not want to compromise on reliability.  All information will be backed up off site additionally.

---

### Post by Zill on 2012-09-09
> **b18turboef said:**
> ...My question to you is, assuming windows 7 professional was free like ubuntu, which OS would you use for a little computer sitting and doing nothing but backups?...
Personally, even if I was paid to install MS Windows, I would still choose to run *only* Linux OS's on my systems.  I have been running such systems for many years now and have had no problems with reliability - they just work!

In your case, as you still intend to retain some Windows systems, it *may* be best for you to "stick with what you know" and use Windows on your backup system.  However, if you are prepared to learn how to configure Linux systems properly, you should find that the performance and reliability you need is more than adequate and leaves most MS systems standing.

---

### Post by Lars Noodén on 2012-09-09
If you want simplicity, ease of use and reliability then Ubuntu wins hands down.  It also wins in flexibility and extensibility, so if you want to add or remove things later, it is straighforward and simple.  Go for it.

---

### Post by drdos2006 on 2012-09-09
Here is a HOWTO which I found comprehensive and invaluable for me to start learning about server requirements. 
Uses Webmin to allow your browser to connect and modify your server settings on your network.


> 
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
"Setting up a Linux Server, Start to Finish, using Webmin". By Kevin Elwood



And on your server..........

```

Logon to your server and download from your server with :
sudo wget http://prdownloads.sourceforge.net/webadmin/webmin_1.590_all.deb

Install with :
sudo dpkg -i webmin_1.580_all.deb

Add extra libraries with :
sudo apt-get -f install

```
Uses a browser pointed to your server to edit files, create shares, startup daemons etc..

regards

---

