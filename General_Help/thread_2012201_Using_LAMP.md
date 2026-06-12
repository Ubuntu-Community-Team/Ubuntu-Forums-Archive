---
title: "Using LAMP"
date: 2012-06-28
forum: General Help
---

### Post by 7o7YlUcb on 2012-06-28
Hi, previously I have used XAMPP on windows for website development but I want to use in in Linux. So I installed the LAMP server using...

     sudo apt-get install lamp-server^

This seemed to work - when I type 127.0.0.1 in firefox I get a page saying "It works!" etc.

But I dont know what to do next. E.g. how to I launch phpmyadmin, where do I place my website files, what configurations do I need to make?

All the tutorials I have read tell me first to run: 
    /opt/lampp/lampp start
but there is no such directory. Maybe the tutorials are for an older version.

Anyone know of a good up todate tutorial for LAMP for Linux noobs?

Thanks.

---

### Post by Doug S on 2012-06-28
I would recommend the Ubuntu server guide for whichever version you are using.
It also conatins links in each section to other valuable resources.
 
[https://help.ubuntu.com/](https://help.ubuntu.com/)
and for 12.04: [https://help.ubuntu.com/12.04/serverguide/index.html](https://help.ubuntu.com/12.04/serverguide/index.html)
and the PDF, which I like so I can print pages and make notes: [https://help.ubuntu.com/12.04/serverguide/serverguide.pdf](https://help.ubuntu.com/12.04/serverguide/serverguide.pdf)
 
Hope this helps.

---

### Post by Cheesemill on 2012-06-28
You've installed a proper LAMP server, not XAMPP.

The web root is /var/www/

PHPAdmin isn't a standard part of a LAMP server, if you want to use it then it has to be installed separately.

Also the '/opt/lampp/lampp start' command is only meant for if you have installed XAMPP, as you have installed Apache, MySQL and PHP separately using the 'sudo apt-get install lamp-server^' command you don't need to do this, your server automatically starts every time you boot.

---

### Post by 7o7YlUcb on 2012-06-28
Thanks [Doug S]("http://ubuntuforums.org/member.php?u=1245983") and Cheesemil. I had got confused with XAMPP and LAMP. As far as I can work out, it seems that XAMPP is better for noobs so I'll uninstall LAMPP and install XAMPP.

---

### Post by Cheesemill on 2012-06-28
The problem with installing XAMPP is that it isn't part of the Ubuntu repositories.

This means that you have to manually keep on top of security patches and software updates for all of the programs that it contains, as well as it installing applications in locations that don't comply with the Ubuntu specifications.

For example the latest version of XAMPP was released over 9 months ago, there will have been any number of vulnerabilities and exploits discovered in it's code since it was released.

If you keep the LAMP installation that you currently have it will automatically stay updated along with the rest of your system as it is integrated into the Ubuntu package management system.

Although it takes a bit more effort to become acquainted with the software I believe it is definitely worth it as you will learn more about how proper web servers on the internet are run.

From the XAMPP site:
> As mentioned before, XAMPP is not meant for production use but only for  developers in a development environment. The way XAMPP is configured is  to be open as possible and allowing the developer anything he/she wants.  For development environments this is great but in a production  environment it could be fatal.   Here a list of missing security in XAMPP: 
 

[LIST=1]
[*]The MySQL administrator (root) has **no** password.
[*]The MySQL daemon is accessible via network.
[*]ProFTPD uses the password "lampp" for user "nobody".
[*]PhpMyAdmin is accessible via network.
[*]Examples are accessible via network.
[*]MySQL and Apache running under the same user (nobody)
[/LIST]

---

### Post by matt_symes on 2012-06-28
Hi

> As mentioned before, XAMPP is not meant for production use but only for developers in a development environment. The way XAMPP is configured is to be open as possible and allowing the developer anything he/she wants. For development environments this is great but in a production environment it could be fatal. Here a list of missing security in XAMPP: 

The MySQL administrator (root) has no password.
The MySQL daemon is accessible via network.
ProFTPD uses the password "lampp" for user "nobody".
PhpMyAdmin is accessible via network.
Examples are accessible via network.
MySQL and Apache running under the same user (nobody)

Which is exactly why you should NOT use it.

Don't get into bad habits from the start.

Kind regards

---

### Post by Baconator507 on 2012-06-28
Hey RevRhubar dont give up on LAMP.

Install phpmyadmin like this
sudo apt-get install phpmyadmin

---

