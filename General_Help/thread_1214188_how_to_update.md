---
title: "how to update?"
date: 2009-07-15
forum: General Help
---

### Post by Arbiter5 on 2009-07-15
how do i go about updating programs like firefox and pidgin?

---

### Post by earthpigg on 2009-07-15
system -> administration -> update manager.

keep in mind that, aside from security updates, ubuntu generally only updates the versions of specific programs at each release: 8.10, 9.04, 9.10, etc.

if you want a version more up to date than what is in the repos, you can go either to the software vendor's website or to getdeb.net.

---

### Post by ramnarayan on 2009-07-15
> **Arbiter5 said:**
> how do i go about updating programs like firefox and pidgin?

go to menu SYSTEM -> ADMINISTRATION -> SYNAPTIC
 make sure you are connected to the internet

reload (it reloads the information) 

the find firefox or pidgin and see if there is a star against them - if so there are updates available - click to install etc

infact while at it update all the other packages.

***
for firefox another way (does not work in 9.04 though)
go to firefox - open the Help Menu and there should be an Update firefox option there (if its misted out then it will not work)

---

### Post by alien8tive on 2009-07-15
```
sudo apt-get update
```

---

### Post by lovinglinux on 2009-07-15
> **earthpigg said:**
> system -> administration -> update manager.

keep in mind that, aside from security updates, ubuntu generally only updates the versions of specific programs at each release: 8.10, 9.04, 9.10, etc.

if you want a version more up to date than what is in the repos, you can go either to the software vendor's website or to getdeb.net.

As earthpigg said above, Ubuntu repositories only includes security updates, until a new Ubuntu release is available. It doesn't upgrade an application just to provide new features for current Ubuntu releases. Which means you cannot upgrade from Firefox 3.0.9 to Firefox 3.5, just from 3.0.9 to 3.0.11. Nevertheless, you can for example install the newest Firefox version side-by-side with the official one.

The 4 most popular methods of installation of Firefox 3.5 (Psychocats, Ubuntuzilla, Repository, Shiretoko/Swiftfox) are available in the "Install Other Versions" section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567). 

There is also a detailed explanation of each installation method provided, comparing the most important differences. I personally tested all of them and they work like a charm, but I recommend methods 1 (Psychocats) and 2 (Ubuntuzilla).

---

