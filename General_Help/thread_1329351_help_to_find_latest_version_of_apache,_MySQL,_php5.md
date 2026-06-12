---
title: "help to find latest version of apache, MySQL, php5"
date: 2009-11-17
forum: General Help
---

### Post by shaon3343 on 2009-11-17
[B][SIZE=2]hi there, 
I'm using Ubuntu 9.04. Can anyone help me to find the repository for apache,MySQL and php5?after updating repo list( [/SIZE][/B][COLOR=DarkOliveGreen]*[SIZE=2]s[/SIZE][SIZE=2]udo apt-get update[/SIZE]*[/COLOR]**[SIZE=2]) I've checked apache2 in the synaptic , but it shows me that the latest version is 2.2.11 . But actually latest version is 2.2.14. So how can i get a latest version of apache2, MySQL, and php5 ? Please help me.[/SIZE]**

---

### Post by Giblet5 on 2009-11-17
The repos have the latest confirmed-stable release for 9.04.

If you want the latest, you must build it from the source code. I don't recommend this unless you are proficient in C and C++, because you will have a great deal of difficulty getting them built and because you'll be supporting them all by yourself.

If you are proficient in C and C++, you'll find that all of these packages are fairly straight-forward builds, but I would stay away from the svn builds as they tend to be buggy.

You can download the source tarballs from the developer's sites.

---

### Post by shaon3343 on 2009-11-17
> **Giblet5 said:**
> The repos have the latest confirmed-stable release for 9.04. 
Thanks for your reply! :p
But Yesterday I've entered "sudo apt-get install mplayer" . then it said mplayer is already the latest version!! then I added mplayer repo. and then i installed the latest version of mplayer. I want to know if there any repository for apache, MySQL, php5 which i've not added and which have the latest version?

---

### Post by Giblet5 on 2009-11-17
> **shaon3343 said:**
> Thanks for your reply! :p
But Yesterday I've entered "sudo apt-get install mplayer" . then it said mplayer is already the latest version!! then I added mplayer repo. and then i installed the latest version of mplayer. I want to know if there any repository for apache, MySQL, php5 which i've not added and which have the latest version?

Ohhhhh. [forehead-smack]

Try [dotdeb]("http://www.dotdeb.org/").

---

### Post by mithun.kamath on 2009-11-17
Try this

    sudo apt-get install mysql-client mysql-server mysql-admin
    sudo apt-get install apache2
    
Also 
Checkthis for PHP

[https://help.ubuntu.com/8.10/serverguide/C/php5.html]("https://help.ubuntu.com/8.10/serverguide/C/php5.html")


Hope that helps

---

