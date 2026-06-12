---
title: "error trying to install themes"
date: 2009-07-09
forum: General Help
---

### Post by Unreal223linux on 2009-07-09
I was trying to install themes from this link:
[http://www.ubuntugeek.com/nice-ubuntu-themes-for-jaunty-and-intrepid-users.html](http://www.ubuntugeek.com/nice-ubuntu-themes-for-jaunty-and-intrepid-users.html)

When I tried to do this command I got an error:
> 
add the GPG key using the following command

    sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0×1781bd45c4c3275a34bb6aec6e871c4a881574de


```

user@user-laptop:~$ sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0×1781bd45c4c3275a34bb6aec6e871c4a881574de 
[sudo] password for user: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --recv-keys --keyserver keyserver.ubuntu.com 0×1781bd45c4c3275a34bb6aec6e871c4a881574de 
gpg: "0×1781bd45c4c3275a34bb6aec6e871c4a881574de" not a key ID: skipping 


```


I managed to get the theme I wanted installed by getting the key from the PPA directly however that error has me a little worried... were any changes made to my computer? I'm a little freaked out that I may have broke something and may not even know untill a problem pops up at an inopportune time.

---

### Post by JohnsShadow on 2009-07-09
your fine they just gave you the wrong key ring

it will not affect your system

if you like themes may i suggest gnome-look.org

---

