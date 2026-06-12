---
title: "Absolute easiest way for a noob to host a simple website from a non server desktop?"
date: 2010-07-31
forum: General Help
---

### Post by Nick_Jinn on 2010-07-31
Are there programs for this? Really really simple page layouts that you can edit and host from a graphical desktop that has your web browsers and Pidgen and VLC media player and everything running on it at the same time?

---

### Post by sf-it-services on 2010-07-31
if you install apache2 and then create your webpages in /var/www  your desktop will in fact become a webserver accesible on port 80 on your IP address (depending on any router config).  You can view your website using the address localhost from that machine.

To have a [www.xxxxxxxx.xxx]("http://www.xxxxxxxx.xxx") website name you will need your details linked to IP address on a nameserver which your registration agent should be able to provide.

I think what you are thinking of with pidgin and vlc will be using the desktop remotely, which is different to just hosting a website.

---

### Post by Nick_Jinn on 2010-07-31
I dont mean using those apps, just illustrating that we are talking about an end user system that also happens to be hosting a site, rather than a dedicated server that isnt intended for personal use.



Thanks.

---

### Post by sf-it-services on 2010-07-31
you may have apache2 installed already, check for a /var/www folder, or type localhost into the address bar of the browser.  

The problem with self hosting are mainly that often dynamic IP addresses are allocated by ISP's so it may change.  the machine with the website files on will have to be on to access the pages.

Hosting the website yourself is not a problem, people often forget that a Server(machine) usually runs many servers, the server being a piece of software that responds to requests not the physical machine. Installing Apache2 will give your machine www server capabilities.

---

### Post by Nick_Jinn on 2010-07-31
Well, I have registered web domains. Will that help? Will they forward traffic to a dynamic IP address?

---

### Post by sf-it-services on 2010-07-31
some ISP's will not re-allocate IP Addresses unless your modem is rebooted, others such as mine although they have dynamic IP Addresses has allocated me a specific one which remains the same for my modem (unless they choose to change it).  I used to host my website by IP address only which was the easiest.  services such as dyndns can be used for dynamic IP name resolution however first I would check you need it.
If you make a note of your IP address and then reboot your ISP Provided modem and see if its changed, it may be that it will not be.  This will not guarantee that it will not change in the future however.

---

### Post by Nick_Jinn on 2010-07-31
Could I use an UbuntuOne account as a stable point of reference between my registered domain name and my PC?

---

### Post by mshenrick on 2010-07-31
I would just use apache2 (put stuff in /var/www)

> **Nick_Jinn said:**
>  Really really simple page layouts that you can edit and host from a graphical desktop that has your web browsers and Pidgen and VLC media player and everything running on it at the same time?

I have no idea how to do this, but it probably involves php or ruby etc. VLC has a server built in I think

---

### Post by sf-it-services on 2010-07-31
I am not to sure about Ubuntu one as I have never used it, but if its a personal cloud as I have just seen and you are making a website visible to the public, then its a different set of issues. as you connect to ubuntu one with your user and pass, it is not IP Address specific.   

Check your Modem to see if the IP Address changes when its rebooted, it should be easy to set a pre-registered web name to direct to your IP on the nameservers available.  Although some ISP's frown upon hosting from within their home Users IP Addresses (Thats why they have business accounts)

---

### Post by nerdy_kid on 2010-07-31
opera has a service built into their browser that turns your pc into a server very easily

---

### Post by stinkeye on 2010-07-31
Yes,have a look at [**_[COLOR="DarkRed"]Opera Unite[/COLOR]_**]("http://unite.opera.com/guide/#enable")
Just had a look at it and was able to set up a music server
that I can access my music from anywhere with a http address.
By default it's private and can only be accessed if you give someone the 
password.

---

### Post by nerdy_kid on 2010-07-31
yeah thats it; really like that idea and would use opera myself if it supported extensions.

---

### Post by Nick_Jinn on 2010-08-01
> **nerdy_kid said:**
> yeah thats it; really like that idea and would use opera myself if it supported extensions.


Who says you cant use both?


Maybe somebody should make a lite weight meta-browser, so you can have all your tabs in the same place but some are run with Chrome and some with Firefox and some with Opera, ect....and you can mix and match the extensions and widgets and add-ons seamlessly via the meta-browser.

---

### Post by stinkeye on 2010-08-01
Another way to do this is if your ISP provides you with free personal webspace.
My Isp gives me 20 mb on an ftp server where I can upload files to.
They give you a http address which connects to the index.html file that you uploaded via ftp.

A few years ago without knowing any html I made a simple website to advertise my work, using a wysiwyg html editor like Kompozer.

Then once made you can upload it using an FTP client like Filezilla.

Check with your Isp and if they provide the service they should have a tutorial.

If not you can do the same thing with opera unite but you just serve the 
web pages from a folder on your computer.
It's something you would only use for family and friends though because when you turn off your computer or close Opera there's no server.

---

### Post by Nick_Jinn on 2010-08-01
I have web hosting with Dreamhost, unlimited domains and 12tb of bandwidth...or is it unlimited now?


Anyway, I am still learning but want to figure out some tools for hosting streaming media from your PC, completely mobile and decentralized.

---

### Post by nerdy_kid on 2010-08-01
> **Nick_Jinn said:**
> Who says you cant use both?


Maybe somebody should make a lite weight meta-browser, so you can have all your tabs in the same place but some are run with Chrome and some with Firefox and some with Opera, ect....and you can mix and match the extensions and widgets and add-ons seamlessly via the meta-browser.

that is a very interesting idea!  would never work though... but cool none the less.  personally i strongly dislike using more then one browser, dont really know why.  like all my stuff in one place i guess...

---

### Post by Nick_Jinn on 2010-08-04
Anything is possible, but it would probably require higher end hardware and more ram.


All it would require is an addon for each of them that allows you to view the contents of a page that is being viewed on another browser....they already have this. I think either firefox or one of the others has one that allows you to open an IE page inside of your firefox tabs. The metabrowser would behave like this but allow you to apply any addon or extension from any of the major browsers all in one place.


I am not a developer, but I believe anything can be done if you put your mind to it.

---

