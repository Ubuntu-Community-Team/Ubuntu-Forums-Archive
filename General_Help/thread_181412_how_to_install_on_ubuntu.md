---
title: "how to install on ubuntu ?"
date: 2006-05-24
forum: General Help
---

### Post by ThaDoctor99 on 2006-05-24
Hi,

i have just begun to run in ubuntu, so i wondered if any could help me to learn to install things on ubuntu.....
Any help appreciated.


Greetings Tobias a.k.a. ThaDoctor99

P.S. I am absolut beginner

---

### Post by seth0x2b on 2006-05-24
Hey.
Simplest way is to use System > Administration > Synaptic Package Manager
The other way(it will soon be the ONLY way you'll use ;) ) is to open up a terminal and use:
sudo apt-get install <package name>
Here's the Apt how-to: [http://www.debian.org/doc/manuals/apt-howto/](http://www.debian.org/doc/manuals/apt-howto/)

Cheers , welcome and good luck ;)

---

### Post by ThaDoctor99 on 2006-05-24
And that is working with a webserver as well, apacha forinstance ?
I would like to get apache installed and begin to write PHP scripts.... :-)

Greetings Tobias a.k.a. ThaDoctor99

---

### Post by aysiu on 2006-05-24
[http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing) is your friend.

---

### Post by nanotube on 2006-05-24
[QUOTE=ThaDoctor99]And that is working with a webserver as well, apacha forinstance ?
I would like to get apache installed and begin to write PHP scripts.... :-)

Greetings Tobias a.k.a. ThaDoctor99[/QUOTE]
yes, it would work for apache as well. see link that aysiu posted about various ways of installing software. but most stuff should be in synaptic.

---

### Post by IYY on 2006-05-24
> And that is working with a webserver as well, apacha forinstance ?
I would like to get apache installed and begin to write PHP scripts....

Yes, you'll find Apache on there.

---

### Post by ThaDoctor99 on 2006-05-24
what about when i should change the chmod value so i can actually write in my apache webserver ?

Greetings Tobias

---

### Post by eentonig on 2006-05-24
When you're apache is installed, it creates a system user and group "www-data" which have full rights on the webroot. You might as well set you user account in this www-data group, so you don't have to chmod or sudo anything when you want write access to this folder.

System\Administration\Users and Groups
Check 'Show all users and groups'
Click on the 'groups' tab.
Selectthe www-data group and click on "properties"
Add yourself to this group.

---

### Post by aysiu on 2006-05-24
[QUOTE=ThaDoctor99]what about when i should change the chmod value so i can actually write in my apache webserver ?

Greetings Tobias[/QUOTE] Just press Alt-F2, type ```
gksudo nautilus
``` and middle-click-drag a folder in your Home folder to /var/www and select **link here**.

---

### Post by ThaDoctor99 on 2006-05-25
It seems now that i can write in my webserver folder, but i cant see my php scripts in firefox :-S, anybody can help me there... ?


Greetings Tobias
any help this far have been appreciated, thanks.

---

