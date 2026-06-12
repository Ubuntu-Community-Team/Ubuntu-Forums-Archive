---
title: "Error installing gcc 4.2 on ubuntu"
date: 2012-09-03
forum: General Help
---

### Post by loremaster on 2012-09-03
Hi guys, not sure if this is the right forum but i really really need some help. Lol.

I am an Ubuntu newbie and just installed this OS.

I am trying to install gcc 4.2 for matlab  2009b since it works with it only and gcc 4.6 or 4.7 doesn't. 

I tried using 

sudo aptitude install gcc-4.2-multilib libstdc++6-4.2-dev


but it keeps saying can't find the package finding the description.


I have already added 
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main to the end of my sources.list but aptitude gives me that error when i try to install gcc 4.2.

Must i download the package first for aptitude to install or aptitude finds it on my behalf?

And for some reasons I am not a superuser when i tried some of the commands like

sudo -get update i think and i get permission denied. Do i need to be a super-user to install gcc?

Any help is appreciated! Once again thanks!
                                                                                                   [IMG]http://ubuntuforums.org/images/rebrand/statusicon/user_online.gif[/IMG]                            [[IMG]http://ubuntuforums.org/images/rebrand/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=12212120")                                                                                    [[IMG]http://ubuntuforums.org/images/rebrand/buttons/edit.gif[/IMG]]("http://ubuntuforums.org/editpost.php?do=editpost&p=12212120")

---

### Post by loremaster on 2012-09-03
Ok i resolved it, apparently i was downloading from the wrong depositary for gcc had to find the right one plus the right package name.

I have a new problem now though when i edited the gcc options file in order for matlab 2009b to recognise gcc 4.2 but i get this error.

I followed the instructions here at 
[http://techify.giridharsweb.com/2012/01/25/installing-gcc-4-2-in-ubuntu/](http://techify.giridharsweb.com/2012/01/25/installing-gcc-4-2-in-ubuntu/)

My Errpr:

cc1plus: warning: command line option ‘-std=c99’ is valid for C/ObjC but not for C++ [enabled by default]

Any help is appreciated! Thanks!

---

