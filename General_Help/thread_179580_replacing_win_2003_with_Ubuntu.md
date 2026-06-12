---
title: "replacing win 2003 with Ubuntu?"
date: 2006-05-20
forum: General Help
---

### Post by closeyourwindows on 2006-05-20
I work at a school were the funds are limited and all the computers are running Win XP Pro and 2000 with a 2003 server.  there are about 45 total computers.  what we are looking to do is do away with the hefty win license and use a linux distro to manage the computers.  right now they are on active directory and I would like to know if this setup is possible using Ubuntu.  The reason I would like to use Ubuntu is that I am most comfortable with it.  I could use freeBSD or something I'm sure but never had any experience with it.  

The computers will stay Win xp and 2000, and there might be a few that are ubuntu as well to make things more difficult.  can anyone point me in the right direction?

---

### Post by JoshHendo on 2006-05-20
I believe this is possible, you could install Ubuntu as a server, though I have no idea how to get the other computers to connect to it, though I am sure it is possible if it is Ubuntu. If they are Windows I am not sure if it is possible.

---

### Post by Sef on 2006-05-20
> The computers will stay Win xp and 2000, and there might be a few that are ubuntu as well to make things more difficult. can anyone point me in the right direction?

Check out Edubuntu.  It is designed for schools.

[http://www.edubuntu.org/]("http://www.edubuntu.org/")

This is from "getting started":

> The first option "Install to hard disk", will install a terminal server. Use this option if you'd like to boot from diskless thin clients into this machine. Note that a terminal server requires at least 150MB RAM per client that will be logging into this server. The server will also need a powerful CPU, such as an Intel Xeon processor. To install a terminal server, simply press ENTER here.

The second option, "Install a workstion", will install a single workstation. This is essentially the same as the first option, except that it doesn't include the terminal server setup, or any other server side software (such as Schooltool). Use the arrow keys to navigate one level down, and press ENTER.

The third option "Install a server", installs a minimal setup, where you can install additional components yourself.

[http://www.edubuntu.org/gettingstarted]("http://www.edubuntu.org/gettingstarted")

---

### Post by gregraubie on 2006-05-20
I am in a similar position to you. (also at a school).

I started looking around for inso the other day and came across this HOWTO:

[http://www.howtoforge.com/samba_setup_ubuntu_5.10]("http://www.howtoforge.com/samba_setup_ubuntu_5.10")

I haven't tried it or anything but perhaps it can give you some more info

---

### Post by No-Brain on 2006-05-20
There is a Server-Talk sub-forum in the Support Forum.  You might be more likely to get help there.  I have interest in this as well, although it is more of a curiosity question.

Roger

---

### Post by kbudurka on 2006-05-21
There is an excellent book that helps you setup a big samba network.
It explains samba fromt he very basics of a simple share, all the way to creating a primary domain controller.

The book is: Samba-3 by example.

I buy most of my books from BookPool - [http://www.bookpool.com](http://www.bookpool.com)
no affiliation, I just like their prices, sales, and website.

Here's a direct-link to the book I recommend:
[http://www.bookpool.com/sm/013188221X](http://www.bookpool.com/sm/013188221X)

---

