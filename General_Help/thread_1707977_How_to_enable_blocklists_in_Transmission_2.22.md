---
title: "How to enable blocklists in Transmission 2.22"
date: 2011-03-16
forum: General Help
---

### Post by cymbaline42 on 2011-03-16
[FONT=Verdana][SIZE=2][FONT=Verdana]Transmission  is a lightweight Bittorrent client that supports multiple operating  systems.  The latest version 2.22 was released on March 4, 2011.  One of  the significant changes in this version is that it the blocklist has to  be configured manually unlike previous versions.  This tutorial helps to explain how to set up  the blocklist feature in Transmission:[/FONT]

[/SIZE][/FONT]

[LIST]
[*][FONT=Verdana][SIZE=2]Open Transmission[/SIZE][/FONT]
[*][FONT=Verdana][SIZE=2]The blocklists can be obtained from either the bluetack or the iblocklist websites.  They should be in a **tar.gz** extension to import into Transmission.  A simple internet search will yield the blocklist URL of your choice. [/SIZE][/FONT]
[*][FONT=Verdana][SIZE=2]Transmission  allows automatic updating from only one blocklist currently, so enter  the URL of your choice into Edit - Preferences - Privacy.  Save and  Close.[/SIZE][/FONT]
[*][FONT=Verdana][SIZE=2]To enable multiple blocklists, download your preferred  file, which should be in a tar.gz extension, and extract it into  ~/.config/transmission/blocklist/ folder.  This will not be  automatically updated, so you must periodically update it by downloading  the file manually and extracting it into the folder.   [/SIZE][/FONT]
[*][FONT=Verdana][SIZE=2]To  check whether the blocklist is being enabled in Transmission, re-start,  and click on Help - Message Log.  You can see that they are being  enabled.[/SIZE][/FONT]
[/LIST]
[FONT=Verdana][SIZE=2]
[FONT=Verdana]P.S:  The blocklist folder might vary if you are using a distribution other than Ubuntu or Linux Mint (I've tried it out only on those two).  [/FONT][/SIZE][/FONT]

---

### Post by Us3r Unfriendly on 2013-01-06
Couldn't you set up crontab to download multiple blocklists to that that block list directory, say multiple lists every half hour or so?

Or

Write a small script to download those scripts every time transmission is started?

I haven't used transmission in quite some time.  I use Tixati, which does allow me to use multiple list every time it's started :D

---

### Post by Bucky Ball on 2013-01-06
***General Help*** is not a 'HowTo' sub-forum. That doesn't exist anymore. Please post this on the Ubuntu Wiki, which is where tutorials go now. Thanks for sharing ...

[https://wiki.ubuntu.com/](https://wiki.ubuntu.com/)

---

