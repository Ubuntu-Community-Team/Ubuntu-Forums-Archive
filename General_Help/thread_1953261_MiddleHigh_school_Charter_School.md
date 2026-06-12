---
title: "Middle/High school Charter School"
date: 2012-04-05
forum: General Help
---

### Post by pmcginnis on 2012-04-05
Hello, I am Director of Technology at a Charter middle / high school.  It has come time for us to renew our microsoft licensing agreement and the idea of going opensource and using edubuntu was brought up.

I am very familiar with active directory and group policy editor in a windows domain, but how does that all work in a linux domain?  Will I have as much control and how easily/quickly could I get this going?

---

### Post by PhantomTurtle on 2012-04-06
I did a little research and I found a product similar to it called DirectControl, made by a company called Centrify. This is their website: [http://www.centrify.com/directcontrol/grouppolicy.asp]("http://www.centrify.com/directcontrol/grouppolicy.asp"). It is not a free piece of software.
> Centrify Suite licenses begin at $65 per workstation and $385 per server for Standard Edition, with discounts for volume purchases. Modules for single sign-on to SAP and web applications are also available.
There is a 30 day trial on which you can test to see if it is what you are looking for and is worth paying for. Look at the website for more details. There might be other methods, that might be easier or won't cost any money, but this is all I have found.

---

### Post by bodhi.zazen on 2012-04-06
It can be done on Linux via OpenLDAP, kerberos, and samba or NFS.

But there is going to be a steep learning curve.

Here is what the RHEL documentation looks like

[http://docs.redhat.com/docs/en-US/Red_Hat_Enterprise_Linux/6/html/Deployment_Guide/ch-Directory_Servers.html](http://docs.redhat.com/docs/en-US/Red_Hat_Enterprise_Linux/6/html/Deployment_Guide/ch-Directory_Servers.html)

[http://www.linuxtopia.org/online_books/rhel5/rhel5_administration/rhel5_s1-ldap-files-schemas.html](http://www.linuxtopia.org/online_books/rhel5/rhel5_administration/rhel5_s1-ldap-files-schemas.html)

For kerberos you have a number of other services to configure ...

So it can be done, but you will be on a learning curve.

---

