---
title: "How can I run my website on a flash drive?"
date: 2011-06-03
forum: General Help
---

### Post by Maheriano on 2011-06-03
I have a client that is a strictly Windows user and I set him up an online quoting system where he can quote construction of buildings for his clients based on current prices of materials. All materials and prices are stored in the database and sometimes he's at a client site where there is no internet so he can't do a quote.

Would the best option here be to install Ubuntu onto a flash drive with Apache and run he can run the browser on his Windows computer but it talks to the MySQL database on the flash drive. Would that work?

---

### Post by linuxinstalledfromhdd on 2011-06-03
It will work for a short limited period of time, and then the flash drive will be unusable.  If the project is important, I wouldn't use anything less than a netbook dedicated to that task. Flash drives are good for a short time, because they wear out. Check out google search engine to learn more about the risks of using Flash Drives for long term use.

---

### Post by Wim Sturkenboom on 2011-06-03
No you can't. Only one OS will be running, either Windows from the HD or Ubuntu from the flash.

You can setup WAMP on the Windows machine.

---

### Post by ruffEdgz on 2011-06-03
> **linuxinstalledfromhdd said:**
> It will work for a short limited period of time, and then the flash drive will be unusable.  If the project is important, I wouldn't use anything less than a netbook dedicated to that task. Flash drives are good for a short time, because they wear out. Check out google search engine to learn more about the risks of using Flash Drives for long term use.

I agree with this comment and it would not be smart to hold anything important on that usb. Stealing a usb drive is as easy as stealing a laptop. Don't use it as a permanent means.

Are you talking about placing the usb Ubuntu onto another computer to run while the client uses their windows machine?

---

### Post by linuxinstalledfromhdd on 2011-06-03
It would be better to simply buy a domain and hosting and build them an online PHP quoting system with a database.  He can be on any computer, anywhere in the world, and login to do his quotes.

---

### Post by Maheriano on 2011-06-03
> **linuxinstalledfromhdd said:**
> It would be better to simply buy a domain and hosting and build them an online PHP quoting system with a database.  He can be on any computer, anywhere in the world, and login to do his quotes.

This is done, it works great. I'm trying to find a solution for when they go to an area without internet, some of these farmers are in the middle of nowhere.

So maybe I don't have to install Ubuntu since they won't be booting into it, they'll be using their Windows machine. But can I put the database on the flash drive somehow? It'll be wiped and reloaded weekly/monthly when there are price changes so long term use isn't a concern. And I'll tell them to get encrypted drives in case they're stolen.

---

### Post by pqwoerituytrueiwoq on 2011-06-03
flash drive with xampp portable - [http://portableapps.com/apps/development/xampp](http://portableapps.com/apps/development/xampp)
if frequently used you may want to use a portable usb hdd

why not just run a server on a laptop in virtual box or on the main OS
to enable server processor a the desktop ubuntu just install apache2 php5 mysql-server php5-mysql

---

### Post by Maheriano on 2011-06-03
How the F do you remember your login name?

---

### Post by linuxinstalledfromhdd on 2011-06-03
> **Maheriano said:**
> This is done, it works great. I'm trying to find a solution for when they go to an area without internet, some of these farmers are in the middle of nowhere.

So maybe I don't have to install Ubuntu since they won't be booting into it, they'll be using their Windows machine. But can I put the database on the flash drive somehow? It'll be wiped and reloaded weekly/monthly when there are price changes so long term use isn't a concern. And I'll tell them to get encrypted drives in case they're stolen.

Ok, I see what you want to do now.  I would probably recommend something like a android system cell phone and an app that runs as a small updating database.  They could be travelling around, and get service from time to time to update the database on that, even if they lose coverage in remote locations.  Or they could update it over public Wifi if they couldn't get service. I bet they have an already existing app for that too.

---

### Post by pqwoerituytrueiwoq on 2011-06-04
> **Maheriano said:**
> How the F do you remember your login name?
autocomplete :)
also
go to advanced search page any type the 1st 3 letters in the username filter

---

### Post by ottosykora on 2011-06-04
>This is done, it works great. I'm trying to find a solution for when they go to an area without internet, some of these farmers are in the middle of nowhere.
<

I dont know what complexity your website has, but I do not see any problem running a website from a local position as usb flash. I am doing it often and did no met any problem so far.
I do not use server active contents however, but for that case someone mentioned xamp ,  but here are other things like baby web server portable
 (  [http://portableapps.com/node/14354](http://portableapps.com/node/14354)  )

as far as the wear of the flash, yes this exiits, but today we have 2011 and not 1998 and this problem is very little relevant with current devices

---

