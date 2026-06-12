---
title: "Problem with using Ubuntu 8.10"
date: 2009-07-04
forum: General Help
---

### Post by scan87 on 2009-07-04
Hi all I am stuck with few problems with my Ubuntu OS but very frustrating problems.....

[COLOR="DarkGreen"]**1.**[/COLOR] My first problem is that I can't install the Orange Mobile Broadband on Ubuntu 8.10, subsequently I can't connect to the internet which is very frustrating.......I just use Mobile Broadband for connecting to the internet........The Orange Mobile Broadband works totally fine in my Vista OS.......Both the OS, Ubuntu and Vista are installed in the same laptop.....

[COLOR="DarkGreen"]**2.**[/COLOR] I am new to Linux.....But I know there is a way of connecting to the desktop or maybe the files located in the Vista OS.........But I am not sure how its done.......Both the OS, Ubuntu and Vista are installed in the same laptop..........

[COLOR="DarkOliveGreen"]**3.**[/COLOR] I am a Web Developer........I would like to develop Web Applications using PHP & MySQL on Ubuntu 8.10..........I heard that Linux is the best OS to develop Web Applications.......I am currently developing Web Applications using WAMP on Windows OS........How can I set up LAMP on Ubuntu.......

Can you please, please help me out with the above three problems, I really want to get started with this Ubuntu thing........it is really eating my head....

[SIZE="4"][COLOR="Red"]THANKS AGAIN[/COLOR][/SIZE]

---

### Post by LoneWolfJack on 2009-07-04
1)
there is no guarantee that you will get your internet to work if you have to use a proprietary software that was built solely for windows. most of the time, you don't need the software provided by your ISP though or there are open source alternatives.

2)
in nautilus, your windows partitions should be listed on the left side. apparently linux is still having issues with the new windows file system though, so I am not sure if it's wise (or possible at all) to access vista partitions

3)
```

sudo apt-get install apache2
sudo apt-get install php5 libapache2-mod-php5
sudo apt-get install mysql-server
sudo apt-get install libapache2-mod-auth-mysql php5-mysql phpmyadmin

```

---

### Post by Nautilus112 on 2009-07-04
Upgrade to Ubuntu 9.04, maybe your problems will be solved.

---

### Post by jdeppel on 2009-07-04
As far as accessing files on your Vista partition, I know some people who create a separate partition using the FAT32 filesystem, as a middle ground to "share" files between Windoze and Linux...you could possibly look into that as well.

---

### Post by scan87 on 2009-07-08
Thank you for all your replies. :grin:

---

