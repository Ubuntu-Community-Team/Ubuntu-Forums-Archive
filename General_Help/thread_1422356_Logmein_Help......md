---
title: "Logmein Help....."
date: 2010-03-05
forum: General Help
---

### Post by RazzyDaz on 2010-03-05
It seems that Logmein will only work with Ubuntu 8.04 and not Karmic.  I have been trying to get Logmein to work for months, no luck!  Thankfully, I still have 8.04 running on an older computer.  I use this on a daily basis, since I own a few businesses and this is how I "check-in."  

  I'm beginning to think it's a Java issue.  I'm using Firefox (Namoroka/3.6.2pre) and Google Chrome.  It seems both browsers are having the same issues.  I have searched the forums and followed how to reinstall Java 10.  Also, there are some sites, where I can't load Javascript.  I'm not really sure how to approach this problem.  I have loaded the Java flash as well!  

If I can't get this to work, I'm going back to 8.04 (NO!).

Thanks,
Raz

---

### Post by rbc on 2010-03-05
[https://secure.logmein.com/labs/](https://secure.logmein.com/labs/)

Scroll down to the bottom and find the *LogMeIn Linux Browser Plugin Preview* section. Download the .deb package and install. This won't help with Chrome though

---

### Post by RazzyDaz on 2010-03-05
I have previously done this, and it still doesn't work.  Any other ideas?

Also, this is what comes up when I try install:

bs@BSimon:~$ sudo apt-get install sun-java6-jre sun-java6-bin sun-java6-plugin
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
bs@BSimon:~$ sudo apt-get install sun-java6-jre sun-java6-bin sun-java6-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-jre is already the newest version.
[COLOR=Black]sun-java6-jre set to manually installed.[/COLOR]
sun-java6-bin is already the newest version.
sun-java6-bin set to manually installed.
sun-java6-plugin is already the newest version.
The following packages were automatically installed and are no longer required:
  libqt4-opengl linux-headers-2.6.31-14 linux-headers-2.6.31-16 libqt4-assistant libqt4-dbus lsb-graphics lsb-desktop m4 ncurses-term libqt4-gui libqtcore4
  libqt4-sql-sqlite lsb libnspr4-dev pax linux-headers-2.6.31-16-generic libqt4-sql libqt4-svg libqt4-xml libqt4-network libqt4-designer libqtgui4
  libqt3-mt libqt4-script lsb-core linux-headers-2.6.31-14-generic firefox-3.6-branding lsb-cxx
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by markackerman8@gmail.com on 2010-04-27
I would also love to find out if anyone has found logmein to work in ubuntu 64 (Lucid of course ha-ha).  I had it working for a day back over a month ago and have not been able to reproduce it.  I have all the java (4) installed and the logmein.deb but it gets all the way to logging in and fails to link ... here is the output ...

"
LogMeIn Remote Control Client
Copyright (C) 2003-2009 LogMeIn, Inc. Patented and patents pending.
Host reports version 982.
Client version 1.0.34.

Connecting...
chris-pc-wuxftsegnm.app01-12.logmein.com, port: 443
Connected.

Negotiating SSL...",   and here is where it fails!  SSL????

any ideas??  and thanks!

---

### Post by 7h3d4rk0n3 on 2010-05-14
I think your answer lies in TeamViewer, which has recently been made for  Linux. It allows you to remotely access any computer in which you have  it installed on. You can also create an account and have a partner list,  which makes connecting to multiple computers very easy without having  to remember the access numbers for separate computers. Hope this helps.

------------------------------------------------------------------------------------------------------

Derik

AKA: ThedarKOne

---

### Post by obscurant1st on 2010-05-14
yeah, why dont u use Teamviewer, they have a beta works with linux. and it works perfectly, i have tried it!! :)

---

### Post by markackerman8@gmail.com on 2010-05-14
Thanks guys, 

In fact I have been using TeamViewer for the past 2 weeks and foir the most part, I am loving it, and other than the fact thati it can handle any combination of Windows, Linux, and (I think) Mac, it has a great file transfer function that is awesome.

Sold....

Mark

---

