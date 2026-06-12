---
title: "Database on my Aspire One netbook"
date: 2012-05-09
forum: General Help
---

### Post by WinfriedG on 2012-05-09
I try to install a database for my personal transactions on my AAO which runs under Lubuntu 11.10

I have libre-office base installed but when I try to save the structure of a table it hangs and is not able to save 
I installed mysql from the synaptic but nothing appeared on my application menu. It seems that I missed to install the GUI or it does not exist. 
I installed  mysql administrator but it asks to connect to a mysql server: what is that? Well in another thread I found out it is in my case localhost. But when I insert the name in the administrator query I get a reply 
```
Could not connect to host 'localhost'.
MySQL Error Nr. 2002
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

Click the 'Ping' button to see if there is a networking problem.
```I clicked the Ping button and it shows a running list fo the following type:
```
64 bytes from localhost (127.0.0.1): icmp_req=28 ttl=64 time=0.098 ms
64 bytes from localhost (127.0.0.1): icmp_req=29 ttl=64 time=0.076 ms
64 bytes from localhost (127.0.0.1): icmp_req=30 ttl=64 time=0.096 ms
64 bytes from localhost (127.0.0.1): icmp_req=31 ttl=64 time=0.079 ms
64 bytes from localhost (127.0.0.1): icmp_req=32 ttl=64 time=0.070 ms

```Any idea what this means?
I have not set up a database since the last 30 years; at that time I used to work extensively with dbase and the first thing one had to do when startig was to define the structure of the database. Here I see no GUI of that kind? 
I assume that I have not the right applications to work with mysql.
Could anybody help? Is there a tutorial for Lubuntu and mysql?

---

### Post by snowpine on 2012-05-09
I think that LibreOffice is a better choice than MySql for creating a home-user database. If you run LibreOffice from the command line, then you will get verbose output you can use to troubleshoot the error. You could also try Gnumeric, it is similar but simpler.

---

### Post by WinfriedG on 2012-05-09
> **snowpine said:**
> I think that LibreOffice is a better choice than MySql for creating a home-user database. If you run LibreOffice from the command line, then you will get verbose output you can use to troubleshoot the error. 
Well I still have the problem with libreoffice base; in the terminal nothing is indicated it just stucks and stops working. Maybe the atom CPU is too weak for this application 

> **snowpine said:**
> You could also try Gnumeric, it is similar but simpler.
Well Gnumeric is a spreadsheet programme; that is not adequate for my project; it should be something like Dbase, a relational database; libreoffice Base would be right if it would work; what I read about mysql it would also suit me but I do not get it running.

So either I will find out what happens with libreoffice-base and get it running or I have to consider giving up my idea to attack my project with a linux operated database. I have also a windows pc; there the database works without problems.[IMG]http://ubuntuforums.org/images/icons/icon10.gif[/IMG] I would be very sorry, since I love my little netbook under Lubuntu.

---

### Post by snowpine on 2012-05-09
Whoops, I mis-spoke about Gnumeric, sorry.

I can confirm that Libreoffice runs fine on my three Atom-based computers. :) (I'm not an Ubuntu user though.) Have you visited Launchpad to check for bug reports?

If you're looking for help administering MySQL then you might be interested in **phpmyadmin**. I believe there is some how-to in the Ubuntu Server Guide?

---

### Post by Zill on 2012-05-10
> **WinfriedG said:**
> ...I have libre-office base installed but when I try to save the structure of a table it hangs and is not able to save...
I use an Asus Aspire One D260-A netbook which has an Atom N450 1.66GHz processor and 1GB RAM.  This works fine with the OpenOffice.org 3.2.1 database.  As LibreOffice is basically a newer fork of OOo I guess this *should* also work OK.

Where are you trying to save the file?  It should be in a directory that you can write to, such as your /home/user directory (or sub-directory).  If you are trying to save the file elsewhere then you are likely to have permissions problems.

I suggest you try creating a short test file with LibreOffice **Writer** and then save it to the *same* directory as your database file.  If this works then it will verify that your directory permissions are OK.

FWIW, I believe using mysql for your task is using a sledgehammer to crack a nut.  This is an "industrial grade" application that is not really appropriate for a small personal database.  OpenOffice/LibreOffice base is far more suitable for this task IMHO.

---

