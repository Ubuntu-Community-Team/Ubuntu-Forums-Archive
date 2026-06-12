---
title: "problems updating"
date: 2012-02-06
forum: General Help
---

### Post by jeff944 on 2012-02-06
Hi 
  I hope someone can help me. I am trying to update my ubuntu and I get this error message "E: The package evince-common needs to be reinstalled, but I can't find an archive for it". I have tried to uninstall and reinstall and get the same error. Thanks to anyone who can help.

---

### Post by maverickaddicted on 2012-02-07
Have you seen these threads -

[http://sathyz.wordpress.com/2011/06/09/ubuntu-gnome3-evince-common-dependency-breaks/](http://sathyz.wordpress.com/2011/06/09/ubuntu-gnome3-evince-common-dependency-breaks/)

[https://bugs.launchpad.net/ugr-meta/+bug/785762](https://bugs.launchpad.net/ugr-meta/+bug/785762)

---

### Post by jeff944 on 2012-02-07
Thanks for the links, but they did not work for me. I am new to ubuntu so i'm still learning. This is the some of the commands i've tried with no luck.


       :~$ sudo apt-get --purge remove evince
[sudo] password for jeff: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package evince-common needs to be reinstalled, but I can't find an archive for it.
         :~$ sudo apt-get --purge remove evince-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package evince-common needs to be reinstalled, but I can't find an archive for it.
          :~$ sudo apt-get install evince
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package evince-common needs to be reinstalled, but I can't find an archive for it.

---

