---
title: "Linux Server + Apache + MySql + Php"
date: 2010-01-27
forum: General Help
---

### Post by D-rock on 2010-01-27
***** If this thread was created in the wrong section, please move - Sorry in advance *****

So I'm totally new when it comes to Linux Servers and PHP Web development but I'm simply in the mood to start something fresh.

A Little background:   I've build my own HTML websites before but found it to be very boring.  I currently work for a software development company and am pretty good at my job.  I've used Ubuntu and all of its flavors in the past but never a Linux Server.  

If building a server wouldn't be my best option or simply a waste of time, I don't mind hearing it.  I deal primarily with IBM Lotus Notes/Domino and it's database design properties.  I'm interested in PHP language for its database properties.  I would like to simply learn a new trait and if it goes anywhere as a side gig or more, that's great.  It would like to re-tool the company website as the CEO is too cheap to pay for a web developer. .. Either way, I'm being proactive and willing to learn.

Does anyone out there have any idea as to the BEST way to approach this?  Does anyone have this kind of setup now?  I simply don't know my options and instead f wasting time, money and energy, I'm curious if anyone else has a good setup and/or knowledge.

With the next few day's I'll be researching my options online and looking for anything that can help me.

Thanks guy -
D

---

### Post by undecim on 2010-01-27
When installing Ubuntu server, you can choose to install a LAMP server, and everything will be set up for you. You can then place your php files in /var/www and visit them by typing your server's IP address in your browser.

You may also want to look at [activating public_html folders]("http://ubuntuforums.org/showthread.php?t=421531"), so that you don't need root privileges every time you want to change a page.

---

### Post by t4thfavor on 2010-01-27
+1 there is a "LAMP Stack" option built in to the installer, you can be up and running in half an hour. PHP is pretty easy to understand, and MySql is just like any other SQL server (except it's free).

Pretty mych any old hardware will work if you don't install the gui. I have a p4 3.4Ghx with 1.5GB ram, that is complete and utter overkill for a home based server.

In the past I have used PIII 600 with 128mb ram for an LAMP server, and though it was a bit mem constrained, it ran perfectly.

---

### Post by D-rock on 2010-01-27
> **undecim said:**
> When installing Ubuntu server, you can choose to install a LAMP server, and everything will be set up for you. You can then place your php files in /var/www and visit them by typing your server's IP address in your browser.

You may also want to look at [activating public_html folders]("http://ubuntuforums.org/showthread.php?t=421531"), so that you don't need root privileges every time you want to change a page.

I've heard of LAMP but I'll research more.  Regarding sharing out the files, that's awesome!  I like the whole disabling of root, makes for easier working.  It's not like my girl would know how to navigate through Ubuntu let alone bust out Sudo.  thank you for the site/link, I'm going to look into it now while I have time.

> **t4thfavor said:**
> +1 there is a "LAMP Stack" option built in to the installer, you can be up and running in half an hour. PHP is pretty easy to understand, and MySql is just like any other SQL server (except it's free).

Pretty mych any old hardware will work if you don't install the gui. I have a p4 3.4Ghx with 1.5GB ram, that is complete and utter overkill for a home based server.

In the past I have used PIII 600 with 128mb ram for an LAMP server, and though it was a bit mem constrained, it ran perfectly.

So I don't necessarily need anything crazy huh, great.  Instead of buying a PC, I mind as well ask the parents if they have my old PC when I used to live at home.  It's decant with about 1.5 gigs of ram but I could always rebuild/add to the Dell.  My company is thinking about buying us some newer & faster laptops ([http://configure.us.dell.com/dellstore/config.aspx?oc=bnc15zc&c=us&l=en&s=bsd&cs=04&kc=inspiron-15z](http://configure.us.dell.com/dellstore/config.aspx?oc=bnc15zc&c=us&l=en&s=bsd&cs=04&kc=inspiron-15z)) for travel and better support.  What do you guys think of VMware and booting up entirely with a flash drive (16/32 gig)?  Is this possible?  Is this out of the norm?  With this, I wouldn't be stuck to any one PC or server.  Any idea's on this idea?  I'm totally shooting in the dark and don't even know if this is possible but I'm simply using my imagination.

Can I give you guys rep on this site?  

/D

---

### Post by john newbuntu on 2010-01-27
Go ahead.  You've chosen a popular and great architecture in the LAMP stack.  With a small learning curve, if you can impress your boss in creating a small prototype, then you-da-man.  Open source, popular, secure, minimum TCO, rich features - what more does your boss needs?

I must admit I have not used Lotus-Notes/Domino.  However, you might want to keep in mind any migration and training costs and time that you will be incur should you chose to move to LAMP.

---

### Post by t4thfavor on 2010-01-27
Lotus/Domino is an groupware server by IBM that "competes" with Exchange. And I assure you, he would save money not using it:)

VMware for a server would be fine, but you can run apache/MySql/PHP on a Windows Box with less overhead than the vm (its called a WAMP stack). I like having a dedicated server so if I have an application to test, I can leave it on for long periods of time without leaving my laptop on.

Like I said any old Dell will work great, and you wouldn't even have to upgrade it.

---

### Post by D-rock on 2010-01-27
> **john newbuntu said:**
> Go ahead.  You've chosen a popular and great architecture in the LAMP stack.  With a small learning curve, if you can impress your boss in creating a small prototype, then you-da-man.  Open source, popular, secure, minimum TCO, rich features - what more does your boss needs?

I must admit I have not used Lotus-Notes/Domino.  However, you might want to keep in mind any migration and training costs and time that you will be incur should you chose to move to LAMP.

Lotus Notes is simple a database/email server.  It can interact between databases just as some companies have tooled DB2 or SQL databases.  We are the underdogs and because our competitors are currently all web based and we are client based, it posses a real threat for future business.

I'm excited, I'll have some free time from traveling and work in general (Summer time is the slowest) and I'd like to be productive.  Your bring a valid point but this would only act as possibly the company website if not my own to tinker with.  The current website is horrible and any changes or improvements would be a positive push in the right direction.  The website now would need to be re-tooled from the top down so the idea of any migrating or converting over wouldn't weigh any consequences here as it would be a simple, unplugging of one server and plugging of another, if you know what I mean.  We employee's don't like the website but would rather it be professionally done.  One guy is busting his chops learning X-Pages within Lotus Notes environment but he don't think he'll do much with it, otherwise it's simply a touch up course as to the new applications from IBM.

I'd like to build my own prototype from home when when I feel knowledgeable and well versed enough to present it to the company, I will do so.  I'd rather my guns are loaded before I present so that I can answer any questions and/or handle any requests from the higher ups.  Again this is simply an idea that I have been considering for the past 3-4 months and I'd like to bring the idea to fruition.

/D

---

### Post by D-rock on 2010-01-27
> **t4thfavor said:**
> Lotus/Domino is an groupware server by IBM that "competes" with Exchange. And I assure you, he would save money not using it:)

VMware for a server would be fine, but you can run apache/MySql/PHP on a Windows Box with less overhead than the vm (its called a WAMP stack). I like having a dedicated server so if I have an application to test, I can leave it on for long periods of time without leaving my laptop on.

Like I said any old Dell will work great, and you wouldn't even have to upgrade it.

Nice, I like it..  I'm sold. :D

---

### Post by D-rock on 2010-01-27
I've been looking at the cheap Mac Mini ( [http://www.apple.com/macmini/](http://www.apple.com/macmini/) ).  It's cheap, very quiet and I wouldn't need to worry about overheating and it has great reviews.  I would run VMWare on it and pretty much set it and forget it.

---

### Post by D-rock on 2010-01-28
So I've picked up my Mac Mini :D and I'm super pumped!  I've purchased VMWare Fusion 3 and am now looking into the LAMP DIY instructions but it's my understanding that Ubuntu 9.10 server comes with PHP 5.0+, MySql and Apache and all I'd need to do is simply download and/or activate through the repository or cmd?

[https://help.ubuntu.com/community/ApacheMySQLPHP#After](https://help.ubuntu.com/community/ApacheMySQLPHP#After) installing MySQL

Within the instructions it says, "When installing from the Ubuntu 6.06 (Dapper Drake) "Server cd", you have the option of choosing to install a LAMP setup at the inital Ubuntu installation screen. That will install apache2, php5 and mysql 5.0."  but that's 6.06 and not 9.10.  I'm just making sure.

Thanks

---

### Post by D-rock on 2010-02-03
BUMP**

So I finally got my Mac Mini 4 gig 2.53 GHz etc and it's now being projected on to my 37 inch LCD tv on my wall.  I'm currently on it now and am very pleased.  Besides all of this, I'm a little stumped on a few UBUNTU 9.10 'things'.  I've installed VMWare Fusion 3 and have downloaded the Linux 9.10 server iso disk and when I install it, I then setup my username and password... Normally on a client machine, the desktop appears after a few different prompts but i'm still in unix/dos world.  It's killing me and I want to start downloaded/installed the PHP, Apache and MySql to create a lamp server. Does anyone know what I'm doing wrong?  I'm totally new to the Linux Server side.

Thanks in advance
D

---

