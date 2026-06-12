---
title: "Web/Mail server advice"
date: 2010-10-05
forum: General Help
---

### Post by DrReaper on 2010-10-05
Hi Everyone,

I have a computer with ubuntu 10.04 installed and it's working great. I want to start to replace my hosting for my website gamersnews.com with this computer. I would like to configure it to be a webserver and email server. I expect it will get a lot of traffic when its flushed out. 

What is the best option for me if I don't want to install ubuntu server on this unit? Can I even make it work without installing Ubuntu server edition? I have a day to day job and I would like to have a Unbuntu computer like this to help people with their Ubuntu workstations. talking them through issues or problems. 

I was looking into LAMP but I don't know if that is the best option.

Thanks for any advice

---

### Post by krishnandu.sarkar on 2010-10-05
You must install LAMP if you intend to use it as web server. But using the same PC for Server and Workstation is not recommended and feasible too.

BTW a real web server needs a lots of things like huge bandwidth, power backup, security solutions, hardware etc.

So think before using your home PC as server.

---

### Post by DrReaper on 2010-10-05
The computer for the most part will just sit there and act as a webserver. I will from time to time jump on it to talk a user through installing a printer or figuring out what choices to make to get something working. I won't be installing any games or even running open office on it.

I expect it will be some time before I get a lot of traffic. At that point I will build a real server.

---

### Post by DrReaper on 2010-10-05
I am installing LAMP as directed before. I get to the message 
IT WORKS!

Then I try to make a page testing.php 

> <?php phpinfo(); ?>I put it in my directory /home/(user)/server (where user is my account name)
It fails every time. I went back to the webserver file and it shows my folder. I am not sure how to troubeshoot it now. I did try to reboot and it still didn't work. all of the examples show the next step and not what to do if it didn't work.

[http://tuxtweaks.com/2010/04/installing-lamp-on-ubuntu-10-04-lucid-lynx/](http://tuxtweaks.com/2010/04/installing-lamp-on-ubuntu-10-04-lucid-lynx/)

---

### Post by DrReaper on 2010-10-05
I am going to scrub it and start over. I won't get to attached to it until I work the kinks out of it.

---

### Post by rbishop on 2010-10-05
Typically on a default LAMP install your web location is /var/www.  On Ubuntu you have a default webpage of /var/www/index.html.  You would just need to move or delete this file to make your index.php file the default.

---

