---
title: "Installtion Help for LAMP"
date: 2010-04-06
forum: General Help
---

### Post by Deepfrost on 2010-04-06
I am trying to install LAMP or XAMPP as it is known. I am reading a book about PHP, MySQL and JavaScript and it tells me to....


[LIST]
[*]Goto [WWW.apachefriends.org/en/xampp-linux.html](WWW.apachefriends.org/en/xampp-linux.html)
[*]Download xampp (which I did)
[*]Open a Linux shell which I assume is a terminal.
[*]Type su and enter admin password. (I don't know mine I guess so I just typed in sudo.)
[*]Type in tar xvfz xampp-Linux-1.7.3a.tar.gz -c /opt   (This is the step I am having a problem with... I believe anyways)
[/LIST]
[CENTER]**This is what I get out of the terminal!**
[LEFT]brian@brian-laptop:~$ sudo tar xvfz xampp-linux-1.7.3a.tar.gz -c /opt
[sudo] password for brian:
tar: You may not specify more than one `-Acdtrux' option
Try `tar --help' or `tar --usage' for more information.
brian@brian-laptop:~$ sudo tar --help


I did read the help and tried a couple things with no success. I would really appreciate some help with this. It is funny sometimes my goal for tonight was to successfully install LAMP but yet I am sitting here typing this. At least this forum is here. Thanks again.
[/LEFT]
[/CENTER]

---

### Post by dominiquec on 2010-04-06
XAMPP is for Windows.

For the basic LAMP installation in Ubuntu, open a terminal and

```
sudo apt-get install apache2 php5 php5-mysql mysql-server
```

In case you're interested, here are my notes: [http://ubuntuliving.blogspot.com/2007/03/lamp-on-ubuntu.html](http://ubuntuliving.blogspot.com/2007/03/lamp-on-ubuntu.html)

For a little more in-depth info: [https://help.ubuntu.com/9.10/serverguide/C/index.html](https://help.ubuntu.com/9.10/serverguide/C/index.html)

---

### Post by Deepfrost on 2010-04-06
Hmmm well seemed to work. I am testing now using the links you provided. You gave me more of a response then I expected and very quick too. Thank you very much. I am confused about xampp being for windows. I am not saying you are wrong in anyway just not sure why the author would state to install LAMP using the link above. I wonder if it is a run around. I feel it might be because it states xampp for Linux like it was made for something else. Anyways Thank you so much!!!

---

### Post by dominiquec on 2010-04-06
My bad: XAMPP is cross-platform, but I always associate it with Windows. :-D

Glad to hear LAMP is working for you.

---

