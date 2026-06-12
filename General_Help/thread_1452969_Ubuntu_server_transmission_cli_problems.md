---
title: "Ubuntu server transmission cli problems"
date: 2010-04-12
forum: General Help
---

### Post by Gareth_2007 on 2010-04-12
hello every one,

right im very new to ubuntu server, but im very interested in learning.

i would like to install transmission cli but im having problems installing it from the internet and installing! what is the apt-get command to install the CLI version of transmission?

thanks

---

### Post by dannyboy79 on 2010-04-12
sudo apt-get install transmission-cli

---

### Post by dannyboy79 on 2010-04-12
if you're unsure of the package you want to download and you're without a gui use aptitude to search. 
sudo aptitude search transmission
then it'll return all package names with the word transmission in it. you can use aptitude install also.
sudo aptitude install transmission-cli

---

### Post by duanedesign on 2010-04-12
Here is a good link with some information compiled from different sources. It is not necessary to add the PPA. Depending on the version of Ubuntu you are running you might get a newer version using the PPA. If you are running a newer version of Ubuntu like Lucid, for example, you can start at sudo apt-get update.

[How-to-Install-Transmission-CLI-to-Ubuntu-Server]("http://philsturgeon.co.uk/news/2009/02/How-to-Install-Transmission-CLI-to-Ubuntu-Server")

---

### Post by lovinglinux on 2010-04-12
Deluge also offers cli interface, web ui and a remote gtk interface. The last one is awesome.

---

### Post by dannyboy79 on 2010-04-12
> **lovinglinux said:**
> Deluge also offers cli interface, web ui and a remote gtk interface. The last one is awesome.

transmission is the same. im biased though, i use transmission

---

