---
title: "Trying to do a mass network install for my classroom"
date: 2006-01-24
forum: General Help
---

### Post by scottie4442 on 2006-01-24
I teach a class on UNIX/Linux and use Ubuntu as the class operating system.  I have downloaded the DVD version of 5.10 and copied it to the server.  I want to setup the DVD so that my classroom machines can access the image, or just all the files from the DVD in a directory on the server, to do an install to each machine.  I do not want to automate this as I have the students do the actual install each semester, I want them to do the whole install I just do not want to have to pass out lots of CD's to them to do it.  I have the install already setup to start from the server (and it works great, I use PXE) but I am not sure how to setup the server as a repository for all the machines, I have not figured out how to  do the server side, I know how to setup the machines to use the server it just does not work.  I know this is possible and I had it working last year with Fedora Core 3, using NFS, but I really want to use Ubuntu, I think it will be easier for my students to learn. 

Scott Adams
Computer Network Instructor
Southeast Arkansas College
Pine Bluff, Arkansas

---

### Post by patrickfromspain on 2006-01-24
No idea on how you could do that. But just a point: I'd burn a bunch of cds and would give them away. Appart from being easier, maybe some of your students would also install it at home. And well, these days the price of 100cds is very low.

Patrick

---

### Post by taurus on 2006-01-24
Or order a bunch of them to be sent to you for free.  That way, you can have your students install at the beginning of the semester and they would get to keep the offical Ubuntu CD as well...  :)

---

### Post by SSTwinrova on 2006-01-24
[QUOTE=scottie4442]I am not sure how to setup the server as a repository for all the machines, I have not figured out how to  do the server side, I know how to setup the machines to use the server it just does not work.[/QUOTE]

Perhaps this might point you in the right direction??

[http://www.us.debian.org/doc/manuals/repository-howto/repository-howto.en.html](http://www.us.debian.org/doc/manuals/repository-howto/repository-howto.en.html)

---

### Post by scottie4442 on 2006-01-25
I have ordered a bunch, and already given them away and had to make a second order (we gave away 100 CD's in under a week, so we ordered 250 more).  I do not mind using the CD's to do the install, but the students have a tendence to not brind their CD's to class for the labs that we do (If you have never taught college, the students can lose things faster than a little kid (not all students just that select few)).  I think the CD route is how I am going to do it for the moment, just was looking for a way that I could keep everything on the server, I can modify one location so that I do not have to do this to 24 individual computers.

---

### Post by tim15856 on 2006-01-25
Try here for a network install [https://wiki.ubuntu.com/Installation/Netboot](https://wiki.ubuntu.com/Installation/Netboot)

---

### Post by nanotube on 2006-01-25
i am not sure if this will be what you need, but try looking at the 'apt-proxy' package. seems like it would help.

---

