---
title: "Add installed packages to ubuntu customization kit"
date: 2010-11-25
forum: General Help
---

### Post by kanishkdudeja on 2010-11-25
ive started using uck..

i hav around 100 packages installed on my system right now..

and when i use uck package manager and click on the required package to install..

it starts downloading it..

i already have all the packages downloaded and installed on my system..

how can i add them to the live cd using the ubuntu customization kit ?

please help

---

### Post by kanishkdudeja on 2010-11-25
bump

---

### Post by elliotn on 2010-11-25
bump

---

### Post by nolag on 2010-11-29
I would love a good answer to this as well, for now I just thought of something (will try it when I get home, don't get mad if it does not work I have not tried it yet).
 
1) download apache tomcat
2) Make a repo in the ROOT directory for tomcat
 
[http://mediakey.dk/~cc/howto-create-your-own-debian-or-ubuntu-package-repository/](http://mediakey.dk/~cc/howto-create-your-own-debian-or-ubuntu-package-repository/)
 
3) make a softlink in the bin part to the spot on your computer with the .deb files (I think it is /var/cache/apt/archives/ need to double check)
 
4) edit your sources.list to first check your repo (put it on top), replace his site in the tutorial with [http://127.0.0.1:8080](http://127.0.0.1:8080)
 
5) run tomcat
 
6) run uck!
 
7) when it is done change back sources.list so you can update :D
 
I will try this later and post if it worked, if you have time try it now and let us know :D. If it dose not work I would say it uses the sources.list on the ubuntu disk, take it out of the iso, change it and make a new iso :P.

---

### Post by kanishkdudeja on 2010-11-29
thanks mate..im sorry..ive uninstalled uck now..i now use remastersys..u check it out..if it does work, den il start using uck again..take ur time..no issues..:)

---

