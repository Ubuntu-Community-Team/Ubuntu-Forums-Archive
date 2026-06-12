---
title: "how to do a clean uninstall of mysql and phpmyadmin on ubuntu 12"
date: 2012-08-16
forum: General Help
---

### Post by cpama on 2012-08-16
hi. 
mysql is giving me grief and the guy who set it up doesn't have all the passwords. 
I want to uninstall and reinstall.  I tried to uninstall by doing: 

apt-get remove mysql-server
apt-get remove mysql-client
apt-get remove mysql-common
apt-get remove phpmyadmin

But what's the best way to get rid of all mysql related folders? 
I'm noticing that they're still there.

I'm running ubuntu 12

Distributor ID: Ubuntu
Description:    Ubuntu 12.04 LTS
Release:        12.04
Codename:       precise

Thank.s

---

### Post by Habitual on 2012-08-17
```
man apt-get 
```
keyword "purge"

---

### Post by Advait on 2013-05-21
I also need to uninstall phpmyadmin from my 12.04. Please explain "man apt-get" and "keyword "purge"". Exactly what command do I enter? Thanks,

---

### Post by mastablasta on 2013-05-21
man apt-get will display documentation/manual for apt-get command. should look something like this: [http://linux.die.net/man/8/apt-get](http://linux.die.net/man/8/apt-get)
using the *purge *keyword you can search this documentation and find out examples how to use purge with apt-get.

you can also look in ubuntu help pages:[URL="https://help.ubuntu.com/community/AptGet/Howto"]https://help.ubuntu.com/community/AptGet/Howto
[/URL]
> 
apt-get purge <package_name>This command completely removes a package and the associated configuration files. Configuration files residing in ~ are not usually affected by this command. 
[LIST]
[*]+ operator 
[LIST]
[*]
[IMG]http://ubuntuforums.org/community/IconsPage?action=AttachFile&do=get&target=example.png[/IMG] If you want to remove package1 and install package2 in one step: 
apt-get remove <package1> <package2>+
[/LIST]
[/LIST]


---

### Post by ibjsb4 on 2013-05-21
I think he was trying to say

```
apt-get remove --purge phpmyadmin
```

You can still have leftover files though.

[https://help.ubuntu.com/community/AptGet/Howto#Removal_commands](https://help.ubuntu.com/community/AptGet/Howto#Removal_commands)

---

