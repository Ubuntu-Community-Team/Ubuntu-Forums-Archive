---
title: "problem with alien"
date: 2010-10-22
forum: General Help
---

### Post by mrodent on 2010-10-22
hello, newish newbie here.

I want to install a freeware front-end/GUI to MySQL.
mysqlcc has been recommended.  Unfortunately it downloads as an rpm package.  Someone on one site did prepare a ready-made .deb for 32-bit ... but when I tried this I got an error message because I am on 10.10 64-bit.

So I did the following with the 64-bit rpm download, working as root.  My input is the stuff in bold: 

root@chris:/home/chris/Desktop# **alien mysqlcc-0.9.8-1.f7.x86_64.rpm** 
warning: mysqlcc-0.9.8-1.f7.x86_64.rpm: Header V3 DSA/SHA1 Signature, key ID 215633c0: NOKEY
[... about 30 similar warnings]
mysqlcc_0.9.8-2_amd64.deb generated
root@chris:/home/chris/Desktop# **dpkg -i mysqlcc_0.9.8-2_amd64.deb** 
Selecting previously deselected package mysqlcc.
(Reading database ... 163631 files and directories currently installed.)
Unpacking mysqlcc (from mysqlcc_0.9.8-2_amd64.deb) ...
Setting up mysqlcc (0.9.8-2) ...
root@chris:/home/chris/Desktop# **cd /usr/bin**
root@chris:/usr/bin# **ls mysql***
mysqlcc
root@chris:/usr/bin# **mysqlcc**
mysqlcc: error while loading shared libraries: libmysqlclient.so.15: cannot open shared object file: No such file or directory

Looked in Synaptic: "libmysqlclient16" is installed... anyone got any idea what's going wrong ... and how to remedy?

---

### Post by TeoBigusGeekus on 2010-10-22
I don't know about mysqlcc, but I've worked for many years with mysql query browser/mysql administrator and I totally recommend them. I think you can find them in the software center.

---

### Post by mrodent on 2010-10-22
Hi,

Thanks for the suggestion which prompted me to get this app up and running.  Yes, this is great for getting to grips with the MySQL databases in one's system... similar things can be accomplished with phpmyadmin, right? (ah, to explain that remark I have to mention that I installed MySQL as part of XAMPP, the ready-made collection of Apache, Mysql, Php, Perl...).

What I was wondering was whether there might be a freeware app out there which helps construct a more interactive GUI for one's databases.  Along the lines of what you can do with MS Access: forms with buttons and tables, etc.  I'm not surprised not to have found this yet, and am currently developing my own fully-fledged app (in java) to do this sort of thing... although something like that is a non-trivial project.

The fact that I have Apache installed means that potentially a web server-client interface might be envisaged ... so you would access your databases through a Web client <--> Web server (Apache) <--> MySQL server type of arrangement.  I was kind of hoping someone might have created something along these lines.  First indications seems not.  

Which leaves me wondering just how, in day-to-day terms, people actually use their MySQL RDBMS?  Because just using the SQL command line would not be all that practical.  Do people typically use some sort of scripts???  Where do you get these from and how do you use them?

---

### Post by mrodent on 2010-10-23
My God, those superheroes at Sun have done it again...!

The answer to what I was looking for is the "final component" of OpenOffice, namely "Base"... Sun's open-source database app.

This page 

http://wiki.services.openoffice.org/wiki/Connect_MySQL_and_Base

explains how you set this up to work with your installed java and your installed MySQL... it takes about 5 minutes to get up and running and designing ... yes, forms, etc., just like Access (only better, obviously, because this is NOT Windoze, NOT Microsoft, NOT crap).

PS TeoBigusGeekus, just in case you come back here: regarding your signature about Autocad and Archicad - I'm probably telling you something you have already known for ages, but have you ever looked at VirtualBox?  Amazingly, also produced by the demigods from Sun.  For years I was prevented from moving to Linux because I have to use dictation software in my work, and nothing comes close to Dragon Naturally Speaking, which is exclusively on the Windoze platform.  Now I run an instance of WXP *inside* my Ubuntu OS, using VirtualBox.  Might be worth a look...

---

### Post by TeoBigusGeekus on 2010-10-23
From Autodesk's site, Autocad Civil 3d 2011 minimum requirements:

> Windows® 7 Enterprise, Ultimate, Professional, or Home Premium (32-bit); Windows Vista® Enterprise (SP1 or SP2, 32-bit); or Windows® XP Professional (SP3, 32-bit).
Intel® Pentium® 4 processor or AMD Athlon, 3.0 GHz or faster; or Intel or AMD dual core processor, 2.0 GHz or faster.
4 GB RAM minimum recommended.
7 GB disk space with 2 GB free after installation.
1,280 x 1,024 true color video display adapter (true color) 128 MB or greater, Pixel Shader 3.0 or greater, Direct3D®-capable workstation-class graphics card. 1,600 x 1,200 or greater recommended. Multiple monitors are supported.
Microsoft® Internet Explorer® 7.0 or later.
DVD drive.

Something similar applies to Archicad.

When using Cad software you want your pc's full capabilities, something which a vm cannot provide - unless you buy a top, 2000 euros machine.
Thanks for the suggestion though and I'm glad you've found what you wanted. :P

---

### Post by perspectoff on 2010-10-23
> **mrodent said:**
>  Now I run an instance of WXP *inside* my Ubuntu OS, using VirtualBox.

How did you do that? Did you take a COA from a retired computer?

Was it easy to get the Virtual instance of XP registered with Microsoft?

---

