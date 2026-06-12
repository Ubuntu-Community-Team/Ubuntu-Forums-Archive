---
title: "Forgotten Windows 2000 password"
date: 2006-04-05
forum: General Help
---

### Post by the_tiger on 2006-04-05
I have been using ubuntu for ages now :D and have forgotten my windows 2000 password for my dual boot :( . Is there a simple way within ubuntu of seeing/resetting windows passwords?

---

### Post by txinga on 2006-04-05
Personally, I use ERD Commander at work. It is great, and expensive. I did a little googling and found this:

[http://www.petri.co.il/forgot_administrator_password.htm](http://www.petri.co.il/forgot_administrator_password.htm)

Lots of info there, this one looks pretty promising:

Austrumi (v0.9.2 - December 2004)
Austrumi is a Linux bootable ISO image for recovering NT passwords and other cool tools and methods, sized for Business Card size CD media (50Mb). It allows you to change any password, including that of the Administrator, on a partition occupied by Windows NT, Windows 2000 or Windows XP. Simply boot the CD and when you get to the initial boot prompt, type:

boot: nt_pass

This will launch a console utility that will detect Windows partitions on the hard disk and provide you with a menu to modify any user or Administrator passwords on the Windows system. It will even give access to the Windows registry for recovery purposes. Quite a handy utility to keep in your wallet (AUSTRUMI is small enough to fit on a business card-size CD) if you are unfortunate enough to having to deal with Windows machines in your line of work.

Read more at [http://sourceforge.net/projects/austrumi](http://sourceforge.net/projects/austrumi)

---

### Post by the_tiger on 2006-04-05
I made a bootable cd from [http://home.eunet.no/~pnordahl/ntpasswd/](http://home.eunet.no/~pnordahl/ntpasswd/)
This worked extremely well allowing me to see all my users and reset the required password. Whilst this is a useful solution I was really wondering if admin management of this sort could be easily acheived from Ubuntu without having to boot from a CD?

---

