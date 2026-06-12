---
title: "How do i install the latest Pidgin messenger"
date: 2012-09-16
forum: General Help
---

### Post by CCgirl6690 on 2012-09-16
Hello everyone , im new here and im not sure if its the right place to ask  i am on Backtrack 5 and i want to install latest pidgin i dunno how , and the ap-get install pidgin command installs an older version and i dunno how to update it , would someone please give me walk through on how to do this by commands or however thanks................

---

### Post by snowpine on 2012-09-16
You can always download the latest Pidgin here: [http://www.pidgin.im/](http://www.pidgin.im/)

Ubuntu users also have the option to use the Pigdin PPA: [https://launchpad.net/~pidgin-developers/+archive/ppa/](https://launchpad.net/~pidgin-developers/+archive/ppa/)

I have no idea whether Ubuntu PPAs will work in Backtrack, use at your own risk!

---

### Post by CCgirl6690 on 2012-09-16
ty for teh reply , but please im a noob i was thinking backtrack is a ubuntu dist , maybenot , but i will need all the commands and anything ,im all new to linux.ubuntu. so ill need more detailed help . thank you so much

---

### Post by snowpine on 2012-09-16
I have never used Backtrack and cannot provide detailed help, sorry.

Since you are totally new to Linux, why not use the stable and supported older version of Pidgin until you know your way around the system?

---

### Post by CCgirl6690 on 2012-09-16
well the older version has issues, but i just dounloaded teh latest pidgin sources its pidgin-2.10.6.tar.bz2 and saved it to my desktop . how do i install it from there? i can manage to uninstall the current version on my os , i will need your help to install that thank you so much

---

### Post by CaptainMark on 2012-09-16
backtrack is entirely compatible with ubuntu ppas ```
sudo add-apt-repository ppa:pidgin-developers/ppa; sudo apt-get update; sudo apt-get upgrade
```

---

### Post by CCgirl6690 on 2012-09-16
oh i love this forum , backtrack forum sucks  ,thanks mark with the reply but do i need to uninstall pigin first , and the commands you gave me are the only ones i need?  im a very newbie  thank you so much , iv never used ppa stuff before thankzzzzzzzzzzzzzzzzzzz

---

### Post by CCgirl6690 on 2012-09-16
Mark?????

---

### Post by CaptainMark on 2012-09-16
no need to uninstall, it just gives update manager access to the newer versions so the pidgin package/s will be kept up to date automatically with your normal system updates

---

### Post by CCgirl6690 on 2012-09-16
Oh to late i uninstalled it , and installed teh ppa package too  now i have the pidgin-2.10.6.tar.bz2 and used tar xvjf pidgin-2.10.6.tar.bz2 then cd pidgin-2.10.6 then ./configure but it gives me this error: configure: error:   You must have GLib 2.16.0 or newer development headers installed to build.  If you have these installed already you may need to install pkg-config so I can find them. -----  what should i do? and how do i install it , mike ,   thank you so much ........................

---

### Post by snowpine on 2012-09-16
You can **ignore** the pidgin-2.10.6.tar.bz2 you downloaded and follow Mike's method instead, much simpler.

---

### Post by CCgirl6690 on 2012-09-16
mark'e method is for when u have it installed and you want to update it , but i have uninstalled it ,so i need to install again  thanks

---

### Post by CaptainMark on 2012-09-16
then use ```
sudo add-apt-repository ppa:pidgin-developers/ppa; sudo apt-get update; sudo apt-get install pidgin
```and the update manager will still keep you up to date with pidgin

---

### Post by CCgirl6690 on 2012-09-16
thanks mark , right before u post , i typed apt-get install pidgin and this times it said connecting to ppa somethign and installed it and i guess its teh latest version this time , thank you again for the help.,,,,,,,,,,,,,,,,,, but something else i dont see an update manager in my OS , i hope PPA will automatically updates pidgin whenever its outdated right?  thanks again

---

### Post by snowpine on 2012-09-16
If Backtrack does not have an update manager then you can try the following terminal commands (they work in Ubuntu, not sure about Backtrack):

```
 sudo apt-get update
sudo apt-get dist-upgrade
```

The first command checks for available updates, the second downloads & installs them. :)

---

### Post by CCgirl6690 on 2012-09-16
what is sudo? i noticed when i dont type that it works too

---

### Post by CaptainMark on 2012-09-16
sudo is what gives you root access (administrator rights) if this command works without sudo then you are logged on permanently as root which is very very inadvisable

i dont know if backtrack automatically logs you on as root but it would not surprise me as backtrack is not intended as an operating system to install permanently, it is designed to be used just as a live cd with the purpose of penetration testing or hacking, i'd recommend reinstalling ubuntu over backtrack and if you regularly require the use of penetration testing software then install it from the ubuntu software centre

---

### Post by CCgirl6690 on 2012-09-16
are you saying its not safe logging in as root? what would happen? thanks

---

### Post by snowpine on 2012-09-16
Lots of good info about logging into Ubuntu as root here:

[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

However Backtrack is designed as a "live" system for security testing (NOT as an everyday operating system for web browsing etc.) and so possibly they may have a different policy on logging in as root, I really don't know.

---

### Post by CaptainMark on 2012-09-16
A lot of live systems have altered root protocols, like logging on as root or having no password for sudo commands, backtrack could be one of them,
the fact that backtrack is meant as a live cd only could also explain its apparent lack of an update manager

---

