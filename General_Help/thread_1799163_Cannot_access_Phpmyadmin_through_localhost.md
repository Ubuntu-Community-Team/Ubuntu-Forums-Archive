---
title: "Cannot access Phpmyadmin through localhost"
date: 2011-07-07
forum: General Help
---

### Post by xdeathcorex on 2011-07-07
Hi, so I've just reinstalled XAMPP in my machine. Now, I can't get phpmyadmin to work.

Before this was okay. But since I lost its password I need to reinstall it again.

Now I got it reinstalled, another problem occured. When I enter localhost/phpmyadmin in my browser, it tells me to open the file with a program which is obviously something must be wrong during the installation or the system is screwed. Here's the screenshot:

[IMG]http://i.imgur.com/DAh3X.png[/IMG]

Another problem is I can't get Apache and MySQL to run using the XAMPP wizard. But by using shell I can get it worked, but when I see the wizard, it just says stopped. What's wrong? Although I have pressed Execute it still can't be run.

[IMG]http://i.imgur.com/BElx9.png[/IMG]

From terminal:
```
me@me-laptop:~$ sudo /opt/lampp/lampp start
[sudo] password for me: 
Starting XAMPP for Linux 1.7.4...
XAMPP: Another web server daemon is already running.
XAMPP: Another MySQL daemon is already running.
XAMPP: XAMPP-ProFTPD is already running.
XAMPP for Linux started.
```

Pls help thanks in advance.

---

### Post by mikejonesey on 2011-07-07
you need to tell apache to process php files as php...

this i belive is usualy done automatically when you install php through package manager

```
sudo apt-get install --reinstall php5
```

---

### Post by xdeathcorex on 2011-07-07
Done that. But nothing changes.

Is there anything or stuff I didn't install yet?

---

