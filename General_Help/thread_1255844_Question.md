---
title: "Question"
date: 2009-09-01
forum: General Help
---

### Post by xdweaver on 2009-09-01
Okay guys and gals. Got a question. 

 First of all I am so new to ubuntu. so that out of the way. my brother up graded to a new pc and gave me his old one, ( Compaq presario sr1365cl) So I installed ubuntu Full disk on it. Now it seems that some of the firmware and drivers did not transfer with the new install. So my question is can i or should i go on to hp and download the drivers, firmware?

  I am not sure you can do that through wine? I just don;t know and would rather ask someone who knows more about this than I. I would like to put this pc in my daughters room ( she like build a bear) please know that i am using ubuntu and all seems to work just can't do the desktop effects and for whatever reason she ( my daughter) tried to go on build a bear and it will not let her login. Any help would be great. Thanks, Dan

---

### Post by SoftwareExplorer on 2009-09-02
Most drivers from Hp are likely to be for windows and wouldn't work under wine. To check for drivers you can install, Go to System->Administration->Hardware Drivers.

---

### Post by earthpigg on 2009-09-02
do not try to use WINE to get hardware drivers to work :D

can you provide more details about what exactly you want to do, please?

i got that you want to run compiz... see if you have any luck in system -> administration -> hardware drivers.

as far as build a bear:

she wants to play games on this website? [http://www.buildabear.com/](http://www.buildabear.com/)

try installing 'ubuntu restricted extras' in the applications -> add/remove programs.

if that doesn't do it, try installing 'sun java 6 runtime' and 'sun java plugin' in add/remove.

you will need to restart firefox for any of those changes to take effect.


note that compiz is not required to play web-browser based video games.

---

### Post by 3rdalbum on 2009-09-02
When you say "some of the drivers and firmware didn't transfer", well, firstly none of the drivers transfer. Windows drivers are useless on Linux, and vice-versa.

Secondly, what exactly isn't working on your machine? Most drivers are built-into Linux and activate automatically, as needed. If there's one particular thing that isn't working, please tell us exactly what it is, and we can give suggestions or advise on how to install a driver if necessary.

---

### Post by xdweaver on 2009-09-02
Thanks, I was not sure, sux to be a newbie! thank you for your time

---

### Post by xdweaver on 2009-09-02
I tried your suggestions, still nothing. I tried ubuntu restricted extras in the applications add remove. I then restarted ubuntu and tried again. nada. So I thought i would do a sudo apt-get update, and I got this message:

 W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages)  404 Not Found [IP: 91.189.88.45 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.
I am not sure but maybe the problem lies there? Any ideas?

---

### Post by StuartN on 2009-09-02
> **xdweaver said:**
> she ( my daughter) tried to go on build a bear and it will not let her login.

buildabear.com requires the Flash player, which is not installed by default in Ubuntu. Go to System->Administration->Synaptic Package Manager, then select and apply the flashplugin-nonfree package. "Nonfree" means that the plugin is not patent/trademark-free, but it does not cost anything.

---

### Post by earthpigg on 2009-09-02
> **xdweaver said:**
> 
```
 W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists***_/edgy/_***universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists***_/edgy/_***universe/binary-i386/Packages)  404 Not Found [IP: 91.189.88.45 80]
```


found your problem, friend.

[http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Release_history](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Release_history)

ubuntu 6.10, edgy eft, is no longer supported.

Ubuntu cannot afford to maintain free-to-use servers for every single release of Ubuntu *forever*, so they do not. (add/remove and synaptic need servers out on the internet to connect to in order to download software).

you can keep your existing 6.10 installs, if you like, but you will not be able to install new software from add/remove programs.

go to ubuntu.com and get one of the two current releases -

8.04, which will be supported until April 2011.
9.04, which will be supported until October 2010.

---

