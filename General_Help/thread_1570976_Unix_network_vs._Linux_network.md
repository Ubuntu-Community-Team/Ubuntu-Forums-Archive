---
title: "Unix network vs. Linux network"
date: 2010-09-08
forum: General Help
---

### Post by jroa on 2010-09-08
I will be required to take a Unix Network Administration class at my college soon for my degree.  I am just wondering how close Unix is to the Ubuntu Server edition.  Would it be worth it for me to download and install Ubuntu Serever ahead of time to get some experience, or should I just dive into Unix with the small amount of Linux experience that I have?  I have my home network set up with both Windows and Linux right now, but I only have 2 running desktops and a few laptops that come and go with my kids.  I am not sure if running the server OS on one of my computers would even give me any experience with so few computers.

I just thought I would see if any of you have experience with both Unix and Linux Servers.

---

### Post by harrismh777 on 2010-09-09
Oh bubba, you know the drill... dude, read the silly-bus and check with your professor man!

But I'll give this the college try for you... by and large unix is unix is unix. If you are familiar with linux you will also be comfortable with an AIX system... or a solaris system... or a Mac OSX system!  The heart of networking on unix is IP.   Unix domain sockets on Unix is pretty much the same as Unix domain sockets on Linux, etc. Network Admin can be drastically different, not because of networking per se (tcp/ip, udp, sockets, etc) but because unix-like systems place familiar things in different places. Once you understand one system, it is usually pretty easy to ramp up to the next one. 

Understand something else about unix... and linux. There really is no real distinction between server and desktop. Some distros like ubuntu (and others) tend to want to make separate distros each geared to a specific pupose... but there is absolutely no reason why your desktop machine, or laptop for that matter, cannot be a full-blown server (back at the lab my desk machine did it all.. and I did all of the client server modeling all on the same machine. 

If you want to have a dedicated "server" for your net admin class and you want to use ubuntu server for that purpose your prof will probably not have a problem with it... BUT I have not read your silly-bus and I have not talked to your prof.    

:p

---

### Post by jroa on 2010-09-09
I have a few semesters before I will take the class, but I thought I could get a heads up before taking it.  I have had several networking classes, which included a class on Windows Server 2008.  The Windows Server version is very similar to the desktop version, but has a ton more functionality specific to servers, so I figured that the Ubuntu Server would be similar.  

I have set my home desktop up as a file server, a print server, and even an internet server, so I know that the desktop version of both Ubuntu and Windows can do a lot of the same stuff as the server versions.  

I was just not sure how close Unix and Linux actually are, and if the server version of Ubuntu was worth practicing on to get some experience that can be used for Unix.

As far as I know, I will not be required to use any of this software at home.  I just thought I would learn on it ahead of time to get a jump on the class.

---

### Post by harrismh777 on 2010-09-09
> **jroa said:**
> I have a few semesters before I will take the class, ... I just thought I would learn on it ahead of time to get a jump on the class.

... couple of books I can recommend to you:

Understanding Linux Network Internals: Guided Tour to networking on Linux
O'Reilly      Christian Benvenuti

Linux Network Administrators Guide: Infrastructure, Services, and Security
O'Reilly      Tony Bautts, Terry Dawson  &  Gregor N. Purdy

---

### Post by jroa on 2010-09-09
Thanks, I will see if I can find either of those books at the library.

---

