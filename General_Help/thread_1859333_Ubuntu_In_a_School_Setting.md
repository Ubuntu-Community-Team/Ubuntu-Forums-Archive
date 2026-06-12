---
title: "Ubuntu In a School Setting?"
date: 2011-10-13
forum: General Help
---

### Post by Spirrwell on 2011-10-13
Alright, I didn't know where to put this exactly, but I'll go with this. I also put the prefix as [other] because I'm not so sure Edubuntu is my best route, because I'm not familiar with it, and we don't use any fancy applications anyway. Also, just as a rant warning, if you want to cut to the questions, skip over to the end.

I go to a real small school made up of 23 students, and I'm the techno geek of the bunch, and every one knows it and I'm also the youngest attending there at the rife old age of fifteen. Introduction aside, I've been hearing that the school is really short on money everywhere I go, and they're using technology, that's seven years old, or if they have newer technology, they don't use it to potential. The first thing that popped to my mind was Ubuntu.

Recently my school got a grant to get iPads, Macs, and such to use. Soon they plan on using them, and the way I see things going, it won't completely replace their age old desktops, or their newer laptops which they've downgraded to Windows XP. I'll be taking some college courses by the end of this year, so as such, people don't really judge me as much in my ability in the field of technology, so I have some influence on it if I push for it. 

My idea is to take advantage of lighter weight Ubuntu system which is free, as well as replace their old Microsoft Office 2003 with OpenOffice, or I belief that Ubuntu now uses LibreOffice. I really would like to add more people to the Ubuntu community.

Here is my questions: 

Creating a server and a web filter?

Currently it seems as if my school computers do a network boot on startup, which to be honest, makes me feel old that I know what it is. Anyway, having some experience with Windows Server I see that it works by creating a LAN version of a domain, and each computer connects, and each student has their own user ID and password to login with. I'm guessing the solution to that would be Ubuntu Server, but I would like a point in the right direction so that I can test something like this on my home network. Next, the web filter. I'm sure that could also be configured with Ubuntu Server, but again, I need a little guidance. I just need a filter to block websites non school related, games, auctions, violence, and etc.

That's all for now, and it's a lot to read, so I should probably spread it out.

---

### Post by Azdour on 2011-10-14
Hi,

So at the moment you have a Windows server and a network with Windows XP machines. Are you looking to just replace the Windows server with Ubuntu (or a flavour of Ubuntu) or are you looking to replace the Windows Server and Windows XP?

If it's the latter - my food for thought is that we install Ubuntu for charity and voluntary organisations. We use an Ubuntu server (10.04) on which we install DRBL ([http://drbl.sourceforge.net/](http://drbl.sourceforge.net/)). All the user accounts are on the server and the computers on the network boot from the Ubuntu Server.

So the computers on the network are fat clients - they use their own processor, memory and hardware (except the local HDD, which can be used for swap space). The operating system and applications come from the Ubuntu Server. All the users home directories are stored on the Ubuntu Server and mounted via NFS ([https://help.ubuntu.com/10.04/serverguide/C/network-file-system.html](https://help.ubuntu.com/10.04/serverguide/C/network-file-system.html)) when they boot.

For us it means that we only need to go to one computer to update the operating system or install new software - the Ubuntu Server. This makes the job of updating and installing new stuff quicker than having to install it on each machine separately.

For web filtering you may be able to install that directly on the Server as well, things like Dans Guardian etc..., although I've never done this. We usually install a separate machine that runs Untangle ([http://www.untangle.com/](http://www.untangle.com/)). It sits between the Ubuntu Server and the Router/Internet. Untangle itself is free and we use the lite package ([http://www.untangle.com/Lite-Package](http://www.untangle.com/Lite-Package)) that is also free to provide web filtering. The downside of using the free package is the page that shows when someone tries to access a blocked site/page does have adverts on. I also note there is an education premium package but this has a cost that needs to be paid either monthly or yearly. 

I'm sure that other people will chime in with their opinions/suggestions as well, as I think there is quite a few different ways you can do what you want to do.

---

### Post by Spirrwell on 2011-10-14
Thank you so much, exactly what I needed, right now I'm asking for replacing both Windows Server and the corresponding Windows XP computers, so you were correct with that route, and it seems like the simpler one so I don't have to worry about incompatibility, I'll be testing all this out tonight, so thank you for your help with the exception that I'll probably be going with Ubuntu 11.04 or 11.10 if it's out of beta, haven't been following 11.10 100%.

---

### Post by collisionystm on 2011-10-14
Also look at Zentyal.

---

### Post by Spirrwell on 2011-10-15
I took a look at Zentyal. It didn't seem to be exactly what I was looking for, but the reason I looked at it now was because Ubuntu Server doesn't have GUI, which unfortunately, I need one as I'm still young and don't understand all the fancy command line stuff and I'm unable to install ubuntu-desktop, gnome, or gnome-core even after enabling universe and multiverse repositories in the sources.list. Is there another Linux OS that's capable of the same things or a way to install a GUI on top of my Ubuntu Server install?

---

### Post by Azdour on 2011-10-17
Hi,

You say you are unable to install the ubuntu-desktop even after enabling the correct repositories. What you do see when you try to run:

```
sudo apt-get install ubuntu-desktop
```

When I first started playing with an Ubuntu Server I also installed the ubuntu-desktop without any problems.

Also, is there any reason why you are going for 11.04 or 11.10 for the Server? I've always gone for the LTS version for stability and longevity, from [http://www.ubuntu.com/business/server/overview:](http://www.ubuntu.com/business/server/overview:)

> Long-term support (LTS) releases, supported for five years, are perfect if you're looking for more stability over a longer period of time.

---

